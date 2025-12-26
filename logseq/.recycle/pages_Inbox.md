query-table:: true
#+BEGIN_QUERY
{:title "🔨 待办事项 (按优先级)"
:query [:find (pull ?b [*])
       :where
       [?b :block/marker ?marker]
       [(contains? #{"NOW" "LATER" "TODO"} ?marker)]
       (not [?b :block/priority "Z"])]  ;; 排除低优先级
:result-transform (fn [result]
        (sort-by (fn [h] (get h :block/priority "Z")) result))
:collapsed? false}
#+END_QUERY
