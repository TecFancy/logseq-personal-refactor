- Active Projects
	- {{query (and (page-property status "DOING") (page-tags [[project]]))}}
	  query-properties:: [:page :tags :status :related-area :updated :objective :deadline :created-at :alias :updated-at]
	  query-sort-by:: page
	  query-sort-desc:: true