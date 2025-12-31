type:: [[Tool]]
related-area:: [[Frontend]]
description:: IndexedDB 的极简封装库，Promise 风格，完美支持 React。

- **[最佳实践](((695146f7-d52b-409e-8de0-cf6fab7f8596)))**
- **React Integration**
	- **useLiveQuery**:
		- 这是一个 Hook，当数据库底层的查询结果变化时，组件会自动重渲染。
		- *Code Snippet*: `const friends = useLiveQuery(() => db.friends.toArray());`