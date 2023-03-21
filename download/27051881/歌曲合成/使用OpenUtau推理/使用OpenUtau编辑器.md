<a name="bYMBe"></a>
## 一、下载适用于DiffSinger的OpenUtau
[https://github.com/xunmengshe/OpenUtau/releases](https://github.com/xunmengshe/OpenUtau/releases)<br />推荐带有DiffsingerPack的整合包<br />如果加载过慢可以右键复制链接使用搭配idm等多线程下载程序进行加速下载<br />![Screenshot_20230223_014117_Edge.jpg](https://cdn.nlark.com/yuque/0/2023/jpeg/34659871/1677087796527-57a56d5a-196b-4517-8dd6-217e887f4cc2.jpeg#averageHue=%23fefefe&clientId=u5c92c280-8bb9-4&from=ui&id=uf71be033&name=Screenshot_20230223_014117_Edge.jpg&originHeight=1064&originWidth=1906&originalType=binary&ratio=2.125&rotation=0&showTitle=false&size=242451&status=done&style=none&taskId=u15c009cd-4a29-4f6e-8e93-afe5561c427&title=)
<a name="FzpzS"></a>
## 二、下载音源，拖入OpenUTAU窗口安装
安装时右上角选择能正常显示的编码，如utf-8

![](https://cdn.nlark.com/yuque/0/2023/png/34659871/1677326124599-416a6011-53a0-4ba0-bd8d-849b80ed042f.png#averageHue=%23f2f2f2&clientId=u50b4645a-ac70-4&from=paste&id=ubccdcfcd&originHeight=819&originWidth=1440&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=u59b1b5cf-dea9-4765-8566-d34df7220d1&title=)

![](https://cdn.nlark.com/yuque/0/2023/png/34659871/1677326124654-0fbd712e-7793-484b-91e3-bd8bae7c1176.png#averageHue=%23f3f3f3&clientId=u50b4645a-ac70-4&from=paste&id=ud733617c&originHeight=819&originWidth=1440&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=u5d757955-0bf2-42f0-88cc-6c609192445&title=)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/34659871/1673335397640-e6bf737d-346e-4b51-b593-9e3d3d41213d.png#averageHue=%23f9f9f9&clientId=u6838c9e4-2da8-4&from=paste&height=628&id=j6w3H&name=image.png&originHeight=785&originWidth=1440&originalType=binary&ratio=1&rotation=0&showTitle=false&size=78219&status=done&style=none&taskId=ua835f8d0-0dcc-40cd-bf0c-e862ef9ea18&title=&width=1152)
<a name="l8YUN"></a>
## 三、选择歌手
在音轨左侧的歌手菜单的“DiffSinger”分类中找到你安装的歌手，选择<br />注：歌词支持汉字或拼音输入，连音符为加号+，呼吸音为AP，停顿为SP 
<a name="CJBH5"></a>
## 说明

- OpenUTAU默认开启自动预渲染，即你每进行一笔编辑，都会立即渲染音频并缓存。如果OpenUTAU卡顿，可在“工具→使用偏好→渲染”中关闭自动预渲染
- DiffSinger相关设置可在“工具→使用偏好→渲染”中编辑：
   - 渲染加速倍数：默认为50倍。降低加速倍数可提高音质，但会使合成速度变慢
   - 默认使用CPU渲染，使用DirectML渲染速度更快。请将“机器学习运行器”设置为directml，GPU选择你的独显（NVIDIA和AMD显卡均支持），**然后重新启动OpenUTAU**

![](https://cdn.nlark.com/yuque/0/2023/png/34659871/1677088239934-9cb238f8-6fba-468f-b118-e513dd48f6da.png#averageHue=%23484745&clientId=u2f319e9d-86e7-4&from=paste&id=u306f7701&originHeight=987&originWidth=786&originalType=url&ratio=2.125&rotation=0&showTitle=false&status=done&style=none&taskId=u87f3a613-6af7-4e82-b1a9-76bfd2f2faa&title=)
<a name="yCt5n"></a>
## 参数
DiffSinger支持以下参数

- 音高曲线
- 音素长度
- DYN（音量曲线）
- GENC（性别，需音源支持，默认可调范围±100相当于∓12半音，正方向为男声（共振峰降低））

参数的可调范围可在钢琴窗左下角的齿轮图标设置<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/34659871/1677088660794-ff4aadfe-5c40-4cc5-88ad-4f738a5ff9d4.png#averageHue=%233e3e3e&clientId=u6a921935-2e49-4&from=paste&height=304&id=u81e95c9a&name=image.png&originHeight=647&originWidth=905&originalType=binary&ratio=2.125&rotation=0&showTitle=false&size=34399&status=done&style=none&taskId=u62b71a6f-4969-4362-b04b-8cde293a160&title=&width=425.88235294117646)
<a name="FB6XA"></a>
## 音素器
目前OpenUTAU for Diffsinger包含4个用于Diffsinger的音素器：

- DIFFS ZH 位于ZH分类，基于OpenUTAU内置的vogen音素模型，无需配置，支持汉语普通话
- DIFFS RHY 位于ZH分类，基于 [Diffsinger rhythmizer音素模型](https://github.com/openvpi/DiffSinger/releases/tag/v1.4.1)，效果更好
- ENUNU X 位于General分类，基于NNSVS音素模型，需要音源开发者适配。适用于ENUNU支持的各种自定义语言。[使用方法](https://github.com/oxygen-dioxide/nnsvs-onnx/wiki/%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95%EF%BC%88%E4%B8%AD%E6%96%87%EF%BC%89)
- ENUNU X EN 位于EN分类，基于NNSVS音素模型，需要音源开发者适配。适用于使用CMUDict的英文音源。[使用方法](https://github.com/oxygen-dioxide/nnsvs-onnx/wiki/%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95%EF%BC%88%E4%B8%AD%E6%96%87%EF%BC%89)
<a name="ndw9l"></a>
## 目前限制

- 暂不支持多说话人混合
