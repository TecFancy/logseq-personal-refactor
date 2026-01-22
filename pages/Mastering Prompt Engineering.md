type:: [[Project]]
status:: active
tags:: [[AI]]

- ## Goal
  query-table:: true
	- 建立一套个人的、可复用的系统化提示词方法论。
	- 沉淀出针对 Coding 和 Writing 的高质量 Prompt Template。
	- 能熟练运用 5-Element Framework （Role, Context, Task, Constraints, Examples）。
- ## Knowledge Base
	- 核心公式
		- ((69702f93-2faa-4c1f-843a-3531c50b845e))
- ## Prompt Snippet Library
	- *在这里存放经过验证好用的片段，方便随时组装。*
	- query-table:: true
	  #+BEGIN_QUERY
	  {:title "Coding Snippets"
	   :query [:find (pull ?b [*])
	           :where
	  
	           ;; 约束：引用了 AI (即 [[AI]])
	           [?b :block/refs ?p]
	           [?p :block/name "ai"]
	  
	           ;; 约束：引用了 snippet (即 #snippet 标签)
	           [?b :block/refs ?m]
	           [?m :block/name "snippet"]
	  
	           ;; 约束：引用了 coding (即 #coding 标签)
	           [?b :block/refs ?c]
	           [?c :block/name "coding"]
	           
	           ;; 约束：在 Journal 中
	           [?b :block/page ?j]
	           [?j :block/journal? true]
	           [?j :block/journal-day ?d]] ;; 获取日期用于排序
	   :result-transform (fn [result]
	                       (sort-by (fn [h]
	                                  (get-in h [:block/page :block/journal-day])) > result)) ;; 按日期倒序
	  }
	  #+END_QUERY
	- query-table:: true
	  #+BEGIN_QUERY
	  {:title "Writing Snippets"
	   :query [:find (pull ?b [*])
	           :where
	  
	           ;; 约束：引用了 AI (即 [[AI]])
	           [?b :block/refs ?p]
	           [?p :block/name "ai"]
	  
	           ;; 约束：引用了 snippet (即 #snippet 标签)
	           [?b :block/refs ?m]
	           [?m :block/name "snippet"]
	  
	           ;; 约束：引用了 writing (即 #writing 标签)
	           [?b :block/refs ?w]
	           [?w :block/name "writing"]
	           
	           ;; 约束：在 Journal 中
	           [?b :block/page ?j]
	           [?j :block/journal? true]
	           [?j :block/journal-day ?d]] ;; 获取日期用于排序
	   :result-transform (fn [result]
	                       (sort-by (fn [h]
	                                  (get-in h [:block/page :block/journal-day])) > result)) ;; 按日期倒序
	  }
	  #+END_QUERY
- ## Action Plan
	- ### Phase 1 - Foundation (Current)
		- DONE 学习并归纳 "Role" 要素
		- DONE 学习并归纳 "Context" 要素
		- DONE 学习并归纳 "Task" 要素
		- NOW 学习并归纳 "Constraints" (约束) 要素
		- LATER 学习并归纳 "Examples" (示例) 要素
	- ### Phase 2 - Practice & Refine
		- LATER 创建 "Logseq Copilot Plugin" 开发的专属 System Prompt
		- LATER 为 "Case Tracker" 项目优化现有的 Cursor/VSCode 提示词
		- LATER 尝试一次 "Prompt Refactoring"：把一次失败的 AI 对话重构为成功的高效提示词
- ## Learning Log / Retrospective
	- *记录每次“AI 没听懂”的失败案例，并分析原因（缺少 Context？Task 不清晰？）。*
	-