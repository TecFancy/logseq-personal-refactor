type:: [[Project]]
status:: active

- query-table:: true
  #+BEGIN_QUERY
  {:title "🔍 BugFix"
   :query [:find (pull ?b [*])
           :where
  
           ;; 约束：引用了 apex
           [?b :block/refs ?p]
           [?p :block/name "apex"]
  
           ;; 约束：引用了 coding (即 #coding标签)
           [?b :block/refs ?m]
           [?m :block/name "coding"]
  
           ;; 约束：内容包含 planning (忽略大小写)
           [?b :block/content ?c]
           [(re-pattern "(?i)bugfix") ?rx]  ;; 使用正则 (?i) 忽略大小写
           [(re-find ?rx ?c)]
           
           ;; 约束：在 Journal 中
           [?b :block/page ?j]
           [?j :block/journal? true]
           [?j :block/journal-day ?d]] ;; 获取日期用于排序
   :result-transform (fn [result]
                       (sort-by (fn [h]
                                  (get-in h [:block/page :block/journal-day])) > result)) ;; 按日期倒序
  }
  #+END_QUERY