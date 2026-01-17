query-properties:: [:page :tags :alias :company :deadline :parent :created-at :updated-at]
#+BEGIN_QUERY
{:title "📂 Active Projects"
 :query [:find (pull ?p [*])
         :where
         [?p :block/name _]            ; 确保 ?p 是一个页面 (Page)
         [?p :block/properties ?props] ; 获取该页面的所有属性集合 ?props

         ;; 1. 匹配 status:: active
         [(get ?props :status) ?status] ; 从属性集中取出 :status 的值
         [(= ?status "active")]         ; 检查值是否严格等于 "active"

         ;; 2. 匹配 type:: [[Project]]
         ;; 注意：当属性值包含 [[ ]] 时，Logseq 数据库通常将其存储为一个 Set (集合)
         [(get ?props :type) ?type]     ; 从属性集中取出 :type 的值
         [(contains? ?type "Project")]  ; 检查集合中是否包含 "Project" 字符串
 ]
 ;; 可选：按页面名称排序
 :result-transform (fn [result]
                     (sort-by (fn [h]
                                (get h :block/name)) result)) 
}
#+END_QUERY

- {{query (and (property :type [[Project]]) (property :status "active"))}}
  query-table:: true
  query-properties:: [:page :deadline :alias]