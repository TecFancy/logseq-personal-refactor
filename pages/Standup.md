query-table:: false
#+BEGIN_QUERY
{:title "✅ Yesterday's CTW Tasks"
 :query [:find (pull ?b [*])
         :in $ ?start ?end ?project   ; 1. 接收项目名称作为输入
         :where
         [?b :block/marker "DONE"]    ; 找完成的任务
         [?b :block/page ?p]
         [?p :block/journal? true]
         [?p :block/journal-day ?d]
         [(>= ?d ?start)]
         [(<= ?d ?end)]
         
         ;; --- 新增约束 ---
         [?b :block/refs ?ref]        ; 这个 Block 必须有引用
         [?ref :block/name ?project]  ; 引用的页面的名字必须等于输入值
         ;; ----------------
         ]
 :inputs [:yesterday :yesterday "ctw"]} ; 2. 在这里输入项目名 (必须全小写!)
#+END_QUERY