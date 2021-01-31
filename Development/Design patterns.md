# Design patterns

Design patterns are solutions to recurring problems in software application development.

They are:
1. Behavioral: it defines how the objects can interact efficiently without being tightly coupled.
2. Creational: it's concerned with the way we create objects. It  applies patterns in the way we instantiate a class.
3. Structural: it's defines how classes and objects are composed to form a larger structure of a application.


## Behavioral

### Observer
It defines a way to update the dependents when there is a state change in another object. It usually contains: `Observer` and `Observable`.
`Observe` subscribes to `Observable` and where there is a change, observable notifies the observers.

** Example:**
```typescript
import Tweet from '../modules/Tweet';

export default interface IObserver {
	onTweet(tweet: Tweet): string;
}
```

```typescript
import Tweet from '../modules/Tweet';

export default interface IObservable {
	sendTweet(tweet: Tweet): any;
}
```

```typescript
import IObservable from '../interface/IObservable';
import Tweet from './Tweet';
import Follower from './Follower';

export default class Author implements IObservable {
	protected observers: Follower[] = [];
	
	notify(tweet: Tweet) {
		this.observers.forEach(observer => {
			observer.onTweet(tweet);
		});
	}
	
	subscribe(observer: Follower) {
		this.observers.push(observer);
	}
	
	sendTweet(tweet: Tweet) {
		this.notify(tweet);
	}
}
```

```typescript
import Author from './Author';
import Tweet from './Tweet';

export default class Follower implements IObserver {
	name: string;
	
	constructor(name: string) {
		this.name = name;
	}
	
	onTweet(tweet: Tweet) {
		return `${this.name} you got tweet => ${tweet.getMessage()}`;
	}
}
```

```typescript
export default class Tweet {
	message: string;
	author: string;
	
	constructor(message:  string, author: string) {
		this.message = message;
		this.author = message;
	}
	
	getMessage(): string {
		return `${this.message} Tweet from Author: ${this.author}`;
	}
}
```


### Strategy
This pattern allows to select the algorithm or strategy at runtime.

eg: can be used for file storage strategy.

** Example:**
```typescript
export default interface IFileWriter {
	write(filepath: string | undefined): boolean;
}
```

```typescript
import IFileWriter from '../interface/IFileWriter';

export default class AWSWriter implements IFileWriter {
	write() {
		console.log('AWS');
		
		return true;
	}
}
```

```typescript
import IFileWriter frin '../interface/IFileWriter';

export default class DiskWriter implements IFileWriter {
	write(filepath: string) {
		console.log('disk');
		
		return true;
	}
}
```

```typescript
export IFileWriter from '../interface/IFileWriter';

export default class Writer {
	protected writer;
	
	constructor(writer: IFileWriter) {
		this.writer = writer;
	}
	
	write(filepath: string): boolean {
		return this.writer.write(filepath);
	}
}
```


### Chain of responsibility
It allows an object to go through a chain of conditions or functionalities, instead of managing all the functionalities and conditions in one place.


## Creational

### Singleton
This pattern implies that there should be only one instance for a class.

eg: can be used to create a database connection class.

**Example:**
```typescript
import { MogoClient, Db } from 'mongodb';

class DBInstance {
	private static instance: Db;
	
	private constructor() {}
	
	static getInstance() {
		if (!this.instance) {
			const url = 'mongodb://localhost:27017';
			const database = 'db_test';
			
			MongoClient.connect(url, (error, client) => {
				if (error) {
					throw new Error('DB error');
				}
				
				this.instance = client.db(database);
			});
		}
		
		return this.instance;
	}
}
```


### Factory
This pattern is used to generate an object instance for a user without exposing any instantiation logic to the client.


### Builder
It allows you to create a different flavors of an object without using a constructor in a class. It solves classes that are hard to maintain, when they have many arguments in your constructor.

** Example:**
```typescript
import User from './User';

export default class UserBuilder {
	firstName = '';
	lastName = '';
	gender = 0;
	address = '';
	country = '';
	isAdmin = false;
	
	constructor() {}
	
	setFirstName(firstName: string) {
		this.firstName = firstName;
	}
	
	setLastName(lastName: string) {
		this.lastName = lastName;
	}
	
	setGender(gender: string) {
		this.gender = gender;
	}
	
	setAge(age: number){
		this.age = age;
	}
	
	setAddress(address: string) {
		this.address = address;
	}
	
	setCountry(country: string) {
		this.country = country;
	}
	
	setAdmin(isAdmin: boolean) {
		this.isAdmin = isAdmin;
	}
	
	build(): User {
		return new User(this);
	}
	
	getAllValues() {
		return this;
	}
}
```

```typescript
import UserBuilder from './UserBuilder;

export default class User {
	firstName: string;
	lastName: string;
	gender: string;
	age: number;
	address: string;
	country: string;
	isAdmin: boolean;
	
	constructor(builder: UserBuilder) {
		this.firstName = builder.firstName;
		this.lastName = builder.lastName;
		this.address = builder.address;
		this.gender = builder.gender;
		this.age = builder.age;
		this.country = builder.country;
		this.isAdmin = builder.isAdmin;
	}
}
```


## Structural

### Adapter
This pattern wraps an incompatible object in an adapter to make it compatible with another class.

** Example:**
```typescript
export default class CustomError {
	message: string;
	
	constructor(message: string) {
		this.message = message;
	}
	
	serialize() {
		return this.message;
	}
}
```

```typescript
export default class NewCustomError {
	message: string;
	
	constructor(message: string) {
		this.message = message;
	}
	
	withInfo() {
		return { message: this.message };
	}
}
```

```typescript
import NewCustomError from './NewCustomError';
// import CustomError from './CustomError';

export default class ErrorAdapter {
	message: string;
	
	constructor(message: string) {
		this.message = message;
	}
	
	serialize() {
		return new newCustomError(this.message).withInfo();
	}
}

```

> examples taken from: [Design patterns in TypeScript and Node.js](https://blog.logrocket.com/design-patterns-in-typescript-and-node-js/)