type:: [[Project]]
alias:: CTW
company:: [[Resource Pro]] 
status:: active

- query-table:: true
  collapsed:: true
  #+BEGIN_QUERY
  {:title "🗓️ CTW 任务追踪 (含父级引用 & 未来7天)"
  :query [:find (pull ?b [*])
         :in $ ?start ?end
         :where
  
         ;; 1. 匹配任务状态 (LATER, NOW, DONE)
         [?b :block/marker ?marker]
         [(contains? #{"LATER" "NOW" "DONE"} ?marker)]
  
         ;; 2. 核心逻辑：匹配页面名称及其别名
         ;; 注意：Logseq 数据库中 name 必须小写
         [?p :block/name ?pagename]
         [(contains? #{"case tracker web" "ctw"} ?pagename)]
  
         ;; 3. 关键魔法：path-refs
         ;; 只要该 Block 的路径上（包括自身、父级、父级的父级）包含该页面，就算命中
         [?b :block/path-refs ?p]
  
         ;; 4. 时间范围限制 (基于日志页面)
         [?b :block/page ?j]
         [?j :block/journal? true]
         [?j :block/journal-day ?d]
         [(>= ?d ?start)]
         [(<= ?d ?end)]]
  :inputs [:-14d :+7d]
  :collapsed? false}
  #+END_QUERY
- ## Important Information
	- Sprint 周期：每周周三开始，两周后的周二结束。
	- Deadline：很大可能延长到年底。
- ## Attachments
	- [Attribute.xlsx](../assets/Attribute_1768274813329_0.xlsx)
- ## Useful Links
  id:: 695c74e5-041b-4718-8511-b4fe96571c3e
	- [Bitbucket](https://bitbucket.org/rspcode/rsp.bpm.casetracker.app/src/main/)
	- [Jira](https://rspproduct.atlassian.net/jira/software/c/projects/PTV2/boards/1252)
	- [Confluence](https://rspproduct.atlassian.net/wiki/spaces/CTW/overview)
	- [PRD](https://rspproduct.atlassian.net/wiki/x/CADEPw)
	- [Microsoft Azure](https://portal.azure.com/#@resourcepro.onmicrosoft.com/resource/subscriptions/89246a81-7dd4-4665-9be9-8fe76418d7a9/resourceGroups/rsp-external/providers/Microsoft.Web/sites/CaseTracker/appServices)
	- [Technology SharePoint](https://resourcepro.sharepoint.com/Tech/SitePages/Home.aspx?RootFolder=%2FTech%2FOperational%20Files%2FBPM%20Applications%2F03%20Case%20Tracker%2FCase%20Tracker%20Web%2FMeeting%20records&FolderCTID=0x0120009705814C52634E47819B79866756BC23&View=%7BC0AE9F1C%2D4FEE%2D4196%2D9154%2D81DF2220A9DA%7D)
	- [Retrospectives](https://rspproduct.atlassian.net/wiki/spaces/PT/pages/396656655/Retrospectives?atlOrigin=eyJpIjoiYzgyZmUxZjI1NmQ5NDczZWJjNmEwODg0MzBkMjA0MDAiLCJwIjoiYyJ9)
	- [Guide SDP](https://resourcepro.sharepoint.com/:w:/r/Tech/_layouts/15/Doc.aspx?sourcedoc=%7B1DE68DB8-25DA-4454-949D-38FD2EAE909B%7D&file=User%20Reference%20Guide_SDP%20CHANGE.docx&action=default&mobileredirect=true&wdOrigin=TEAMS-MAGLEV.null_ns.rwc&wdExp=TEAMS-TREATMENT&wdhostclicktime=1769065105488&web=1)
	- [Apex Components Library](http://rsp-nexusserver:8082/)
- query-table:: true
  query-properties:: [:block :page]
  #+BEGIN_QUERY
  {:title "🔍 Planning Meetings"
   :query [:find (pull ?b [*])
           :where
  
           ;; 约束：引用了 CTW
           [?b :block/refs ?p]
           [?p :block/name "ctw"]
  
           ;; 约束：引用了 meeting (即 #meeting 标签)
           [?b :block/refs ?m]
           [?m :block/name "meeting"]
  
           ;; 约束：内容包含 planning (忽略大小写)
           [?b :block/content ?c]
           [(re-pattern "(?i)planning") ?rx]  ;; 使用正则 (?i) 忽略大小写
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
- query-table:: true
  #+BEGIN_QUERY
  {:title "🔍 Training Meetings"
   :query [:find (pull ?b [*])
           :where
  
           ;; 约束：引用了 CTW
           [?b :block/refs ?p]
           [?p :block/name "ctw"]
  
           ;; 约束：引用了 meeting (即 #meeting 标签)
           [?b :block/refs ?m]
           [?m :block/name "meeting"]
  
           ;; 约束：内容包含 training (忽略大小写)
           [?b :block/content ?c]
           [(re-pattern "(?i)training") ?rx]  ;; 使用正则 (?i) 忽略大小写
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
- query-table:: true
  #+BEGIN_QUERY
  {:title "🔍 Review Meetings"
   :query [:find (pull ?b [*])
           :where
  
           ;; 约束：引用了 CTW
           [?b :block/refs ?p]
           [?p :block/name "ctw"]
  
           ;; 约束：引用了 meeting (即 #meeting 标签)
           [?b :block/refs ?m]
           [?m :block/name "meeting"]
  
           ;; 约束：内容包含 review (忽略大小写)
           [?b :block/content ?c]
           [(re-pattern "(?i)review") ?rx]  ;; 使用正则 (?i) 忽略大小写
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
- query-table:: true
  #+BEGIN_QUERY
  {:title "🔍 Sync Meetings"
   :query [:find (pull ?b [*])
           :where
  
           ;; 约束：引用了 CTW
           [?b :block/refs ?p]
           [?p :block/name "ctw"]
  
           ;; 约束：引用了 meeting (即 #meeting 标签)
           [?b :block/refs ?m]
           [?m :block/name "meeting"]
  
           ;; 约束：内容包含 sync (忽略大小写)
           [?b :block/content ?c]
           [(re-pattern "(?i)sync") ?rx]  ;; 使用正则 (?i) 忽略大小写
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