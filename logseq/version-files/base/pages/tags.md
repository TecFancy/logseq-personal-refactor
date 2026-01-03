- 动作与行为的分类容器，用于 Journal 打标签统计，约定使用**小写**形式。
- | **维度** | **Activity Tags** |
  | ---- | ---- | ---- |
  | **创造/产出** | `[[coding]]`, `[[designing]]`, `[[writing]]` |
  | **输入/学习** | `[[reading]]` (也适用于看电影/展), `[[review]]` |
  | **管理/规划** | `[[planning]]`, `[[finance]]`, `[[life]]` |
  | **身心/连接** | `[[health]]`, `[[social]]` |
- {{query (page-property :type [[tags]])}}
  query-properties:: [:page :type :alias :desc :created-at :updated-at]