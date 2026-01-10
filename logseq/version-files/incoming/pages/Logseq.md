type:: [[Tool]]

- query-table:: true
  #+BEGIN_QUERY
  {:title "🔍 Snippets"
   :query [:find (pull ?b [*])
           :where
  
           ;; 约束：引用了 Logseq (即 [[Logseq]])
           [?b :block/refs ?p]
           [?p :block/name "logseq"]
  
           ;; 约束：引用了 snippet (即 #snippet 标签)
           [?b :block/refs ?s]
           [?s :block/name "snippet"]
           
           ;; 约束：在 Journal 中
           [?b :block/page ?j]
           [?j :block/journal? true]
           [?j :block/journal-day ?d]] ;; 获取日期用于排序
   :result-transform (fn [result]
                       (sort-by (fn [h]
                                  (get-in h [:block/page :block/journal-day])) > result)) ;; 按日期倒序
  }
  #+END_QUERY