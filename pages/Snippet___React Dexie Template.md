related-project:: [[Learn IndexedDB]]

- **Description**
	- 一个标准的 Dexie + React setup 模板。
- **Code**
	- ```ts
	  // db.ts
	  import Dexie, { type EntityTable } from 'dexie';
	  
	  interface Friend {
	    id: number;
	    name: string;
	    age: number;
	  }
	  
	  const db = new Dexie('FriendsDB') as Dexie & {
	    friends: EntityTable<Friend, 'id'>
	  };
	  
	  db.version(1).stores({
	    friends: '++id, name, age' // Primary key and indexed props
	  });
	  
	  export { db };
	  ```