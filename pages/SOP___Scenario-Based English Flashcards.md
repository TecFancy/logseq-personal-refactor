## 1. Purpose (目标)
	- 建立一套通用的口语内化流程，将任何来源（课程、美剧、播客）中的地道表达，转化为**“场景反应直觉”**。从“背单词”转变为“在特定语境下产生沟通意图”。
- ## 2. Core Principles (核心原则)
	- **Context First (语境优先)**：决不记录孤立的单词，必须还原**沟通意图**或**触发场景**。
	- **Output Oriented (输出导向)**：闪卡正面必须是“我想表达什么（意图）”，而非“这个英文是什么意思（翻译）”。
	- **Atomic Design (原子化)**：一张卡片只解决一个具体的沟通痛点。
- ## 3. The Workflow (CODE System)
- ### 3.1 Capture (收集)
- **Trigger (触发时机)**：当你在任何材料中遇到觉得“地道”、“没想到可以这样说”或“解决了某个沟通卡点”的句子时。
- **Action (动作)**：
	- 在当天的 `Journal` 或具体的 `[[Source/来源页]]`（如 `[[Course/Fluent English]]`）中快速记录。
	- **必填**：复制英文原句 + 简要备注当时的语境（谁对谁说，为了什么）。
- ### 3.2 Organize (整理/归位)
- 遵循 **PARA** 法则确定卡片存放位置：
	- **Projects (项目)**：用于有明确进度或截止日期的课程（如 `[[Project/Business English Course]]`）。
	- **Areas (领域)**：用于长期技能积累（如 `[[Area/English Skills]]` 或 `[[Area/Vocabulary]]`）。
	- **Resources (资源)**：用于被动消费的素材（如 `[[Resource/Ted Talks]]`, `[[Book/Atomic Habits]]`）。
- ### 3.3 Distill (提炼/制卡)
	- 将原始笔记转化为符合 Logseq 格式的**标准场景闪卡**。
	- #### Flashcard Structure (卡片结构模板)
		- ```md
		  - **[场景标签] 具体的沟通意图/中文描述** #card
		  	- **Target English Expression (地道表达)**
		  	- **💡 Tips & Nuance (技巧与解析)**：
		  		- **Why (选词逻辑)**：为什么用这个词？（例如 `letdown` vs `disappointment` 的区别）。
		  		- **Usage (用法)**：搭配、时态、语体（正式/随意）。
		  		- **Context (语境)**：（可选）记录原文的出处背景。
		  ```
	- #### Scenario Tags Standardization (场景标签规范)
		- 使用固定的前缀来加速大脑的索引分类（建议按需建立自己的标签组）：
			- `[Emotion]` (情绪：开心、失望、愤怒...)
			- `[Social]` (社交：打招呼、道别、邀请、拒绝...)
			- `[Opinion]` (观点：同意、反对、夸奖、吐槽...)
			- `[Logic]` (逻辑：解释原因、总结、转折...)
			- `[Work]` (职场：会议、邮件、汇报...)
	- ### 3.4 Express (内化/复习)
		- 利用 Logseq 的 `Flashcards` 功能进行主动回忆，执行 **“3秒反应环”**：
			- **Recall (回想)**：看到正面的 `[场景] 意图`，必须在 **3秒内** 大声说出英文。
			  logseq.order-list-type:: number
				- *卡顿或错误？* -> 标记为 `Hard` / `Again`。
			- **Shadow (跟读)**：翻开背面，大声朗读英文表达 **3遍**，尽量模仿原声语调。
			  logseq.order-list-type:: number
			- **Generate (生成)**：**最关键的一步！** 阅读 `💡 Tips` 后，立刻结合自己的生活实际，用这个表达**造一个新句子**。
			  logseq.order-list-type:: number
- ## 4. Maintenance (维护与归档)
	- **Weekly Review (周回顾)**：浏览 `[[Area/English Skills]]` 或你的 `[[Source]]` 页面。
		- **Refactor (重构)**：合并相似的卡片（例如将所有关于“婉拒”的表达聚合在一起）。
		- **Link (连接)**：使用 `[[Topic]]` 双链将新卡片关联到已有的知识网络中。
		- **Archive (归档)**：当一个 `[[Project]]`（如某门课程）结束时，将其移动到 `[[Archive]]`，但保留 `#card` 标签，确保它们依然会出现在你的每日复习队列中。