# 基于实时视频分析的入侵监测系统设计与实现

## 一、项目背景
基于实时的视频流,利用图像识别功能,自动检测视频中的运动物体。包括后端数据处理和前端 web 页面实时显示结果, 广泛应用在小区入侵监测,智能家居的安防,老人智能看护等领域; 加入人脸识别系统，结合其他的智能产品，实现高度自动化的物联网自动化运行环境。同时支持异常图像上传至云服务器,可以配合手机APP,实现全方位,实时监控的目的。 

---

## 二、硬件

- 控制系统：Raspberry Pi3；

- 信息采集：Pi camera；

<div align=center><img height="150" src="http://static.zybuluo.com/TangWill/mmrkgojknahihs4juif0uxb7/image_1defagdvg1vbaidhle54qq1259.png"/></div>


---

## 三、主要技术

- 基于深度图像处理框架 open cv 和数据计算模块 numpy

- 	人脸识别技术
-	Python 语言应用程序开发
-	编写web 端，实现数据实时展示

---

## 四、项目介绍

在需求分析阶段，将项目应用场景主要确定为仓库监控管理并可拓展为博物馆监控管理，实现包括但不限于如下功能：

- 监控端（Raspberrry Pi3、Opencv、JetBrains PyCharm）
- - 对仓库的实时监控
  - 对监控视频中移动物体的分析
  - 向服务器推送视频流和包含图像、分析结果的 json 数据包
  - 心跳包上报等
- 服务器端（Websocket、Tomcat、IntelliJ IDEA）
- - 对监控端发送的数据进行解析和分析
  - 对用户数据进行存储和维护
  - 数据的可视化
  - 根据异常数据通过短信等形式向用户发送警报
  - 根据数据实现断点续传等
- 客户端（Vue渐进式开发框架、Nuxt.js轻量级应用框架、JetBrains WebStorm ）
- - 将账号与设备绑定
  - 登录或直接打开网页查看实时监控
  - 查看月度安全报告等

![](http://static.zybuluo.com/TangWill/sw5opqzft80959h3s2x8um05/%E5%9B%BE%E7%89%871.png)

---

## 五、客户端展示

下面从客户端的角度，结合项目在特定需求背景下实现的特色功能，对项目进行展示。

> 主界面

主页面由三个部分组成，分别为左侧的实时监控，右侧的入侵记录和右上角的导航菜单。

![](http://static.zybuluo.com/TangWill/bh1nnaez8x4qbkc0ocp1qe0q/%E7%94%A8%E6%88%B7%E6%89%8B%E5%86%8C.jpg)

- 实时监控

  当树莓派监控端处于开启状态，用户可以在“实时监控”模块则到实时控的画面。通过 MJPEG 的编码格式，监控画面的延迟大概在1s左右。

- 入侵记录

  入侵记录表分为入侵时间、危险级别、类别、详情四个栏目。
  其中危险级别和类别的判断标准如下表：

| 等级 |              描述              |
| :---: | :---: |
|  A   |     监测到五人以上人类活动     |
|  B   | 监测到五人以下三人以上人类活动 |
|  C   |    监测到三人及以下人类活动    |
|  D   |         监测到非人异物         |


用户点击相应的“详情”按钮，即可得到该次闯入时的监控视频截图。如下图所示。

![](http://static.zybuluo.com/TangWill/pwn4snechua4whjtvjvnfndq/%E7%94%A8%E6%88%B7%E6%89%8B%E5%86%8C.jpg)

- 导航菜单

  - 管理设备

    当仓库无人监管时，用户可以启动入侵报警开关。当入侵报警开关启动后，若监控端监视到有闯入，页面则会提示报警信息，并且会将闯入信息和闯入监控视频截图展示在入侵记录表格中。如果已添加联系人，系统会给联系人发送信息。
    当仓库有人监管时，用户则可以禁用入侵报警开关，不影响页面任何操作。

    ![](http://static.zybuluo.com/TangWill/y8sw0zi2ybs6dduzu7c8ahoo/%E7%94%A8%E6%88%B7%E6%89%8B%E5%86%8C.jpg)

- 添加联系人

  针对同一个仓库，用户可以添加个数上限为5的联系人，输入联系人姓名与联系人电话，在监控端识别到入侵时发送短信提醒用户，该功能用于在仓库有人闯入时，即便无人观看实时监控，也能及时收到提醒。

  ![](http://static.zybuluo.com/TangWill/xnxke63y71r47l1bgo1u9z2d/%E7%94%A8%E6%88%B7%E6%89%8B%E5%86%8C.jpg)

> 月度安全报告

月度安全报告页面由两个部分组成，分别为左侧的数据展示和右侧的高频入侵警告。

- 数据展示
  左侧数据栏为用户展示了本月的入侵总次数，高频入侵时间和具体的时间分布图。用户可根据展示的入侵数据进行分析，从而更好地提高安保效率。
- 高频入侵警告
  系统会从数据库里的所有截取到的入侵截图进行分析比对查找相似图片，并展示在高频入侵警告里。用户可以对于高频入侵图片上的人或物相应地提高警力。

---

## 六、文档展示
<div align="center"><img src="http://static.zybuluo.com/TangWill/emxb3zjwe1w9cvl8ydbz3gvn/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20200413103203.jpg" alt="02" width="28%" height="28%" />   <img src="http://static.zybuluo.com/TangWill/7ydjlugpaau70ao8unw2y1ii/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_202004131032031.jpg" alt="03" width="28%" height="28%" />    <img src="http://static.zybuluo.com/TangWill/efq4xiuxl4mm2tk8vflzs2z0/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_202004131032032.jpg" alt="04" width="28%" height="28%" />    <img src="http://static.zybuluo.com/TangWill/j2thvvr3owk1s9v4d15k8iin/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_202004131032033.jpg" alt="05" width="28%" height="28%" />    <img src="http://static.zybuluo.com/TangWill/1lk5j0wra4x5bqan3c2bn2d0/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_202004131032034.jpg" alt="06" width="28%" height="28%" /></div>
