So, what exactly is a `class`? That’s not an entirely new language-level entity, as one might think.

Let’s unveil any magic and see what a class really is. That’ll help in understanding many complex aspects.

In JavaScript, a `class` is a kind of function.

The basic syntax is:

```javascript
class MyClass {   
	// class methods   
	constructor(name, age) { 
		// values will go inside the constructor function
		this.name = name;
		this.age = age;
	}   
	method1() { ... }   
	method2() { ... }   
	method3() { ... }   
	... 
}
```

Then use `new MyClass()` to create a new object with all the listed methods.

The `constructor()` method is called automatically by `new`, so we can initialize the object there.

```javascript
class User {
	constructor(name) {
		this.name = name;
	}

	sayHi() {
		alert(this.name);
	}
}

let user = new User("John");
user.sayHi();

```