# 基于实时视频分析的入侵监测系统设计与实现（项目简介）


---
## 一、项目介绍
---
基于实时的视频流,利用图像识别功能,自动检测视频中的运动物体。包括后端数据处理和前端 web 页面实时显示结果, 广泛应用在小区入侵监测,智能家居的安防,老人智能看护等领域; 加入人脸识别系统，结合其他的智能产品，实现高度自动化的物联网自动化运行环境。同时支持异常图像上传至云服务器,可以配合手机APP,实现全方位,实时监控的目的。 

---
## 二、硬件
---
- 控制系统： Raspberry Pi3；
- 信息采集：	Pi camera，支持红外功能；
<div style="background-color:none;height:150px;text-align:center;"><img src="http://static.zybuluo.com/TangWill/mmrkgojknahihs4juif0uxb7/image_1defagdvg1vbaidhle54qq1259.png" /></div>

---
## 三、主要技术
---
- 	基于深度图像处理框架 open cv 和数据计算模块 numpy
- 	人脸识别技术
-	Python 语言应用程序开发，提供 Restful 接口调用
-	编写web 端或app 端程序，实现数据实时展示
