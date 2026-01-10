query-table:: false
#+BEGIN_QUERY
{:title "📅 那年今日"
 :query [:find (pull ?b [*])
         :in $ ?today
         :where
         [?b :block/page ?p]       ; 找到所有块所在的页面 ?p
         [?p :block/journal? true] ; 确保这个页面是“日记”页面
         [?p :block/journal-day ?jd] ; 获取该页面的日期 ?jd
         [(- ?today ?jd) ?diff]    ; 计算今天和那天的差值
         [(mod ?diff 10000) ?rem]  ; 核心魔法：取模运算
         [(= 0 ?rem)]              ; 如果余数为0，说明月和日相同，只是年份不同
         [(> ?diff 0)]]            ; 排除今天自己
 :inputs [:today]                  ; 输入今天的日期
 :collapsed? false}                ; 默认展开
#+END_QUERY