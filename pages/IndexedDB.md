tags:: [[JavaScript]], [[Resource]] 
related-area:: [[Area/Frontend]]
alias:: IDB
description:: 浏览器原生的事务型对象数据库 (NoSQL)。

- **Core Concepts (From NotebookLM)**
	- **Database**: 也就是 DB 本身，通过 `open` 请求打开。
	- **Object Store**: 数据的存储桶，类似于关系型数据库的 Table。
	- **Transaction**: 所有读写操作必须在事务中完成。
		- *Insight:* 事务是依附于 Event Loop 的，如果 process 闲置，事务会自动 commit。这意味着 `await` 之后可能导致事务失效（这是原生 API 的大坑）。
	- **Versioning**: 只有在 `onupgradeneeded` 事件中才能修改数据库结构 (Schema)。
- **NotebookLM Q&A**
	- Q: 为什么我们需要 Dexie 而不是直接用 IndexedDB？
	- A: 原生 API 是基于事件的 (Event-based)，会导致 "Callback Hell"；且事务管理极其繁琐。