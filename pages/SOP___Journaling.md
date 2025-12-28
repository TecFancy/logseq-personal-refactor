related-area:: [[Area/KM]]
related-template:: [[Template/Journal]] 
description:: 日记驱动开发 (JDD) 的核心操作指南与规范
updated:: [[Dec 28th, 2025]]

- **1. 核心理念 (Philosophy)**
	- **流式记录 (Stream First)**: 不要纠结分类，先记录。日记是“时间流”，Page 是“知识库”。
	- **扁平化 (Flat Structure)**: 拒绝深层缩进。任务尽量保持在第二层。
	- **链接即整理 (Link as Structure)**: 通过 `[[Project]]` 和 `#Tag` 将看似散乱的日记自动聚合到对应的维度。
- **2. 每日工作流 (Daily Workflow)**
	- **🌞 Morning Routine (启动)**
		- **清空 Inbox**: 检查昨天未完成的任务 (`TODO`)，决定是 `DONE`、`CANCELED` 还是延期。
		- **检查看板**: 点击 `[[Project]]` 页面，通过 Query 表格查看哪些项目状态是 `[[DOING]]`。
		- **浏览 SOP**: 快速扫一眼本页面（特别是 Activity 列表），找回状态。
	- **💼 Work Stream (沉浸)**
		- **记录原则**: 任何耗时超过 15 分钟的动作，都值得记录。
		- **标准格式**: `时间 + 动作描述 + [[Project/Name]] + #ActivityTag`
		- *Example*: `10:30 重构鉴权模块逻辑 [[Project/Refactor-Auth]] #Coding`
	- **🌙 Evening Review (关机)**
		- **状态更新**: 如果某个 Project 到了里程碑，去项目页面更新 `status` 或 `deadline`。
		- **任务迁移**: 尽量不要让今天的页面留有 `TODO`。未完成的要么改为 `DOING` (明天继续)，要么移动到明天的日记中。
- **3. 标签与链接规范 (Linking Rules)**
	- **Project (项目归属)**
		- 使用 **双括号** `[[Project/Name]]`。
		- *含义*: "我正在为这个项目添砖加瓦"。
	- **Activity (动作/上下文)**
		- 使用 **井号标签** `#Tag`。
		- *含义*: "我当下处于什么状态/在做什么类型的活动"。
		- *注意*: 所有的动作标签应预先定义在 `[[Activity]]` 体系中，避免标签泛滥。
- **4. 动作标签字典 (Activity Dictionary)**
	- *遇到不知道打什么 Tag 时，请查阅此表：*
	- **💻 Tech & Work (产出)**
		- `#Designing`: **设计阶段**。画架构图、写技术方案、API 定义、UI 走查。
		- `#Coding`: **实现阶段**。写代码、Debug、重构、提交代码。
		- `#Review`: **复盘阶段**。Code Review (CR)、测试验收、部署发布。
		- `#Meeting`: **沟通**。站会、需求评审 (配合 `[[Meeting/Name]]` 使用)。
	- **🧠 Learning & Growth (输入)**
		- `#Reading`: **阅读**。看技术书、博客、文档，也包括看小说。
		- `#Writing`: **写作**。写 SOP、博客、非技术文档。
	- **🏠 Life & Management (生活)**
		- `#Planning`: **规划**。整理任务、排期、周报、思考下一步。
		- `#Health`: **健康**。健身、运动、冥想、就医记录。
		- `#Finance`: **财务**。记账、理财、副业收入核算。
		- `#LifeAdmin`: **杂务**。缴费、家务、跑腿等维持性事务。
		- `#Social`: **社交**。陪伴家人、聚会。
- **5. FAQ (常见问题)**
	- **Q: 临时的一个小 Bug 修复，不属于任何大项目，怎么办？**
		- A: 不需要强行关联 `[[Project]]`。直接记录：`14:00 修复登录页样式错乱 #Coding #BugFix`。
	- **Q: 笔记层级太深怎么办？**
		- A: 始终保持**扁平**。如果笔记内容很长，点击该 Block 前面的圆点进入**聚焦模式 (Zoom In)** 书写，写完退出来，保持日记页面整洁。