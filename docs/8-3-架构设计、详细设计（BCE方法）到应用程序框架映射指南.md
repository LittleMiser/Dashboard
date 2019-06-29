# 架构设计、详细设计（BCE方法）到应用程序框架映射指南
## 1. 逻辑架构
逻辑架构由四层模型（表示层、业务层、服务层、持久化层）构成。

### 1.1 表示层
- 学生使用 Web 作为表示层，提供用户发布任务子系统、用户领取任务子系统、用户管理任务子系统。
- 机构使用 Web 作为表示层，提供机构发布问卷子系统、机构管理问卷子系统。

### 1.2 业务层
按业务功能服务划分：用户管理模块、快递管理模块、问卷管理模块

### 1.3 持久化层
MongoDB 提供了数据的持久化服务

## 2. 框架目录设计
### 前端
```
├── LittleMiser //前端页面
│   ├── WJinfo //问卷填写页面
│   │   ├── WJinfo.html //问卷填写页面结构文件
│   │   ├── WJinfo.css //问卷填写页面样式文件
│   │   └── WJinfo.js  //问卷填写页面逻辑文件
|   |
│  	├── createExpress //快递单创建页面
│   │   ├── createExpress.html //快递单创建结构文件
│   │   ├── createExpress.css //快递单创建样式文件
│   │   └── createExpress.js  //快递单创建逻辑文件
|   |
│  	├── createWJ //问卷创建页面
│   │   ├── createWJ.html //问卷创建结构文件
│   │   ├── createWJ.css //问卷创建样式文件
│   │   └── createWJ.js  //问卷创建逻辑文件
|   |
│  	├── ExpressDetail //快递单详情页面
│   │   ├── ExpressDetail.html //快递单详情结构文件
│   │   ├── ExpressDetail.css //快递单详情样式文件
│   │   └── ExpressDetail.js  //快递单详情逻辑文件
|   |
│  	├── getExpress //快递单获取任务页面
│   │   ├── getExpress.html //快递单获取任务结构文件
│   │   ├── getExpress.css //快递单获取任务样式文件
│   │   └── getExpress.js  //快递单获取任务逻辑文件
│	│
│ 	├── getQuestion //问卷获取任务页面
│   │   ├── getQuestion.html //问卷获取任务结构文件
│   │   ├── getQuestion.css //问卷获取任务样式文件
│   │   └── getQuestion.js  //问卷获取任务逻辑文件
│	│
│  	├── manageExpress //快递单管理页面
│   │   ├── manageExpress.html //快递单管理结构文件
│   │   ├── manageExpress.css //快递单管理样式文件
│   │   └── manageExpress.js  //快递单管理逻辑文件
│	│
│ 	├── manageQuestion //问卷管理页面
│   │   ├── manageQuestion.html //问卷管理结构文件
│   │   ├── manageQuestion.css //问卷管理样式文件
│   │   └── manageQuestion.js  //问卷管理逻辑文件
│	│
│ 	├── page_1//首页页面
│   │   ├── page_1.html //首页结构文件
│   │   ├── page_1.css //首页样式文件
│   │   └── page_1.js  //首页逻辑文件
│	│
    │ 	├── personinfo //个人信息页面
│   │   ├── personinfo.html //个人信息结构文件
│   │   ├── personinfo.css //个人信息样式文件
│   │   └── personinfo.js  //个人信息逻辑文件
│	│
│ 	├── register //登录注册页面
│   │   ├── register.html //登录注册结构文件
│   │   ├── register.css //登录注册样式文件
│   │   └── register.js  //登录注册逻辑文件
│	│
│ 	├── statistics //问卷统计页面
│   │   ├── statistics.html //问卷统计结构文件
│   │   ├── statistics.css //问卷统计样式文件
│   │   └── statistics.js  //问卷统计逻辑文件
    │	│
│ 	├── index //登录页面
│   │   ├── index.html //登录结构文件
│   │   ├── index.css //登录样式文件
│   │   └── index.js  //登录逻辑文件
│	│
│ 	├── image // 使用的背景图
│	│
└── .DS_Store
```

### 后端
```
└──Backend：服务端开发的源码
|    ├─models
|    |    ├─db.js
|    │    ├─express.js
|    │    ├─paper.js
|    |    ├─user.js
|    ├─routers
|    |    ├─createPaper.js
|    │    ├─expr.js
|    │    ├─fillPaper.js
|    |    ├─getPaperInfo.js
|    |    ├─managePaper.js
|    │    ├─user.js
```

## 3. 与 ECB 关系
ECB 中：
- Entity：代表系统数据，如：问卷、快递等。
- Boundary：与用户的接口，如：界面、网关、代理等。
- Controller：在 Boundary 和 Entity 中衔接的媒介，编排来自 Boundary 的命令的执行。

Entity 包含：
- 服务器框架目录设计中，models 目录下定义了所有服务器与 MongoDB 相关的实体，承载系统数据。

Controller 包含：
- 服务器框架目录设计中，router 目录下定义了所有的相关内容，它们接收来自接口的命令，获取或更新模型或其他请求。

在本系统中，Boundary有两个部分：

- Web 程序用户界面（学生/机构）
- 本地服务器