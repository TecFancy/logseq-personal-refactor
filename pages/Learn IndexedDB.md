type:: [[Project]] 
deadline:: [[Jan 4th, 2026]]
status:: active

- **Objective**
	- 掌握 IndexedDB 核心机制，精通 Dexie.js + React 最佳实践。
- **🗓️ Sprint Tasks (LATER/NOW)**
	- **Phase 1: 原生原理 (Based on MDN)**
		- NOW 🟢 阅读 NotebookLM 总结的 "IndexedDB 事务模型" #Reading
		  :LOGBOOK:
		  CLOCK: [2025-12-29 Mon 13:07:48]
		  :END:
		- LATER 手写原生 `open` 和 `upgrade` 逻辑，体验版本控制 (Versioning) 的痛苦 #Coding
	- **Phase 2: Dexie 实战 (Based on Dexie Docs)**
		- LATER 🟢 学习 `db.js` 单例模式的最佳实践 #Reading
		- LATER 在 React 组件中实现 `useLiveQuery` 实时监听数据变化 #Coding
	- **Phase 3: Demo Output**
		- LATER 🚀 输出一个 "离线 Todo List" Demo #Coding
		- LATER 归档代码片段到 `[[Snippet/React-Dexie-Template]]` #Coding
- **📚 Resources (NotebookLM Context)**
	- **Uploaded Sources:**
		- 📄 [IndexedDB API (MDN)](https://developer.mozilla.org/zh-CN/docs/Web/API/IndexedDB_API)
		- 📄 [使用 IndexedDB (MDN)](https://developer.mozilla.org/zh-CN/docs/Web/API/IndexedDB_API/Using_IndexedDB)
		- 📄 [Dexie.js Best Practices](https://dexie.org/docs/Tutorial/Best-Practices)
		- [📄 Get started with Dexie in React](https://dexie.org/docs/Tutorial/React)
	- **Key Links:**
		- [NotebookLM 笔记本链接](https://notebooklm.google.com/notebook/0565afa9-4c9a-4964-a402-e39e1e61d6a8?authuser=1)
-
- query-table:: true
  query-sort-by:: page
  query-sort-desc:: true
  #+BEGIN_QUERY
  {:title "📝 Daily Log & Insights (From Journals)"
   :query [:find (pull ?b [*])
           :where
           ;; 1. 筛选状态：必须是 LATER, NOW 或 DONE
           [?b :block/marker ?marker]
           [(contains? #{"LATER" "NOW" "DONE"} ?marker)]
           
           ;; 2. 筛选关联：必须链接到 [[Project/Learn IndexedDB]]
           [?b :block/refs ?p]
           [?p :block/name "project/learn indexeddb"] ;; 注意：这里必须全部小写
           
           ;; 3. 筛选来源：Block 所在的页面必须是 Journal
           [?b :block/page ?page]
           [?page :block/journal? true]]
   ;; 4. 排序：按日记日期倒序排列（最新的在最上面）
   :result-transform (fn [result]
                       (sort-by (fn [h]
                                  (get-in h [:block/page :block/journal-day]))
                                > result))
   :breadcrumb-show? false}
  #+END_QUERY