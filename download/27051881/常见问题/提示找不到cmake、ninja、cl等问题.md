*本页教程由至精至简贡献

- 需要安装Microsoft Visual Studio 2019（MSVC v142）或2022（MSVC v143），如未安装请使用Visual Studio Installer结合以下说明安装
   - 必选项
      - MSVC v142/v143 - ...
      - Windows 10 SDK ...
      - 实施调试器
      - C++ 分析工具
      - 用于 Windows 的 C++ CMake 工具
   - 其他项与 C++ Windows 开发相关，可以不选

![3Y8QN)4CI}06VVFY19D$R{9.png](https://cdn.nlark.com/yuque/0/2023/png/34659871/1674893768894-f4c508f0-d238-40a8-9c63-e68f511a7708.png#averageHue=%23eaeaea&clientId=uf60ebeb2-0629-4&from=paste&height=720&id=ue39e84ed&name=3Y8QN%294CI%7D06VVFY19D%24R%7B9.png&originHeight=900&originWidth=1600&originalType=binary&ratio=1&rotation=0&showTitle=false&size=195801&status=done&style=none&taskId=ub0c53cc5-d5d3-4e7b-9be7-4c9bb1c7f50&title=&width=1280)

- MSVC是微软Visual Studio的C/C++编译器，它不像MinGW那样直接把自己放在系统Path中，因为它有四个分身，分别是x64和x86各自的本架构编译与互相交叉编译，所以我们需要使用微软提供的脚本来初始化终端上下文。
- Python 使用包管理器`pip`安装工具时，有时需要从源码编译，此时可能检测不到 MSVC 的环境，需要手动启动环境，如果出现类似找不到`cmake`、`ninja`、`cl`、`link`...等命令，很大概率是没有检测到 MSVC 环境导致的。
<a name="HgwYi"></a>
## 启动环境步骤

1. 在左下角点击智能搜索，输入	`x64`

![image.png](https://cdn.nlark.com/yuque/0/2022/png/34683583/1670942079261-4437ec2a-adc6-4a94-81f0-a6070453abbb.png#averageHue=%23a8ab77&clientId=uc3b81e0c-f868-4&from=paste&height=104&id=u7caea7e5&name=image.png&originHeight=130&originWidth=448&originalType=binary&ratio=1&rotation=0&showTitle=false&size=18469&status=done&style=none&taskId=ua6ef4502-8846-4354-93a7-09b81372083&title=&width=358.4)

2. 如果安装了MSVC编译器，那么一般会出现这个首选

![image.png](https://cdn.nlark.com/yuque/0/2022/png/34683583/1670942196586-3ab9dbb7-e0b3-494a-8a06-eaf382e29db5.png#averageHue=%23434342&clientId=uc3b81e0c-f868-4&from=paste&height=262&id=UliYE&name=image.png&originHeight=328&originWidth=978&originalType=binary&ratio=1&rotation=0&showTitle=false&size=147953&status=done&style=none&taskId=u0f1c9de3-1bf5-4b5f-b19d-df714264352&title=&width=782.4)

3. 单击打开它，会发现弹出了一个命令行窗口，并且提示设置环境完成

![image.png](https://cdn.nlark.com/yuque/0/2022/png/34683583/1670942378597-5d96dd05-0f81-4828-b08b-921e5cf419e7.png#averageHue=%23454240&clientId=uc3b81e0c-f868-4&from=paste&height=154&id=u655c175d&name=image.png&originHeight=192&originWidth=735&originalType=binary&ratio=1&rotation=0&showTitle=false&size=16718&status=done&style=none&taskId=uc27d007a-01e4-4da6-80db-e31b5f40238&title=&width=588)

4. 我们输入`where cl`，会发现微软编译器`cl.exe`已在当前环境中

![image.png](https://cdn.nlark.com/yuque/0/2022/png/34683583/1670942437399-b9b1af9a-5f81-4147-9480-e60f056bd096.png#averageHue=%23373533&clientId=uc3b81e0c-f868-4&from=paste&height=204&id=uc751135d&name=image.png&originHeight=255&originWidth=1155&originalType=binary&ratio=1&rotation=0&showTitle=false&size=27346&status=done&style=none&taskId=u9fcc33b5-e6df-49b3-a0f4-2bca28b911f&title=&width=924)

5. 如果你需要在别的终端中（比如IDE中）设置此环境，那么需要找到`vcvarsall.bat`的路径

![image.png](https://cdn.nlark.com/yuque/0/2022/png/34683583/1670942512347-80595634-5ace-49f3-a3d1-30318f927284.png#averageHue=%23474747&clientId=uc3b81e0c-f868-4&from=paste&height=251&id=u8f32f57f&name=image.png&originHeight=314&originWidth=426&originalType=binary&ratio=1&rotation=0&showTitle=false&size=75579&status=done&style=none&taskId=u5c3ff8bc-5311-406a-baee-316a758ff97&title=&width=340.8)

6. 对这个脚本快捷方式右键-属性

![image.png](https://cdn.nlark.com/yuque/0/2022/png/34683583/1670942587697-6c2539db-9cfe-4a88-8559-c66adcbfa91b.png#averageHue=%23f8f6f5&clientId=uc3b81e0c-f868-4&from=paste&height=186&id=u4c91a1ee&name=image.png&originHeight=233&originWidth=1068&originalType=binary&ratio=1&rotation=0&showTitle=false&size=30939&status=done&style=none&taskId=ud334215d-7f26-4e32-954e-dbeca12f7c2&title=&width=854.4)

7. 它的原身是一个bat脚本，这个快捷方式就是调用cmd启动这个脚本，只需要将`目标`一栏中所有的内容复制到你的新终端（如果是Powershell，那么需要把`%comspec%`改为`cmd`），然后运行即可

![image.png](https://cdn.nlark.com/yuque/0/2022/png/34683583/1670942636362-c1399881-b185-43e9-bfee-3579162061e3.png#averageHue=%23f4f3f3&clientId=uc3b81e0c-f868-4&from=paste&height=638&id=uae4b4610&name=image.png&originHeight=798&originWidth=583&originalType=binary&ratio=1&rotation=0&showTitle=false&size=37841&status=done&style=none&taskId=u1a6deafa-0e59-4f7f-89b8-99379e5a478&title=&width=466.4)<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/34683583/1670942829628-77179de0-2c98-48bd-94ce-828f237d09b2.png#averageHue=%231d1d1d&clientId=uc3b81e0c-f868-4&from=paste&height=634&id=u4dc51c30&name=image.png&originHeight=792&originWidth=1483&originalType=binary&ratio=1&rotation=0&showTitle=false&size=59914&status=done&style=none&taskId=u382023bc-38e1-405f-90be-6cabb33a1b8&title=&width=1186.4)
<a name="xoTYZ"></a>
## 完毕
