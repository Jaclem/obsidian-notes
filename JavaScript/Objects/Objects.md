A property is a “key: value” pair, where `key` is a string (also called a “property name”), and `value` can be anything.

## [Literals and properties](https://javascript.info/object#literals-and-properties)

We can immediately put some properties into `{...}` as “key: value” pairs:

```javascript
let user = {     // an object   
	name: "John",  // by key "name" store value "John"   
	age: 30        // by key "age" store value 30 
};
```

The value can be of any type. Let’s add a boolean one:

`user.isAdmin = true;`

To remove a property, we can use the `delete` operator:

`delete user.age;`

We can also use multiword property names, but then they must be quoted:

```Javascript
let user = {   
	name: "John",   
	age: 30,   
	"likes birds": true  // multiword property name must be quoted 
};
```


# Accessing information in an object

To access the value of the key `likes birds` we need to use bracket notation such as:

`console.log(user["likes birds"])`

There are also 2 ways to get information out of an object: dot notation and bracket notation.

```javascript
// dot notation
myObject.property // 'Value!'

// bracket notation
myObject["obnoxious property"] // [Function]
```

## [Property value shorthand](https://javascript.info/object#property-value-shorthand)

In real code, we often use existing variables as values for property names.
For instance:

```javascript
function makeUser(name, age) {  
	return {     
		name,    
		age,    
		// ...other properties   
	}; 
}  

let user = makeUser("John", 30); 
alert(user.name); // John
```


## [Property existence test, “in” operator](https://javascript.info/object#property-existence-test-in-operator)

### Check if key exists in an Object
There’s also a special operator `"in"` to test if keys in an object exist.
The syntax is:

```javascript
let user = { name: "John", age: 30 }; 

alert( "age" in user ); // true, user.age exists 
alert( "blabla" in user ); // false, user.blabla doesn't exist
```

## [The "for..in" loop](https://javascript.info/object#forin)
### [[Loops]]

We can also loop through all the keys in an object by using `for...in`.

```javascript
let user = { 
	name: "John", 
	age: 30, 
	isAdmin: true 
}; 

for (let key in user) { 
	// keys 
	alert( key ); // name, age, isAdmin // values for the keys 
	alert( user[key] ); // John, 30, true 
}
```

## Constructor Notation

Constructor Notation simplifies making multiple objects of the same thing, for instance if we wanted to add multiple users it would be repetetive to create whole seperate objects for each user.

So we can set up an object constructor function
This function takes perameters that will be in the object itself and can be referenced later `User(name, age, isAdmin)`

We can use the `this` keyword to refer to the object that we're inside of
The function looks something like this:
```Javascript
function User(name, age, isAdmin) {
	this.name = name;
	this.age = age;
	this.isAdmin = isAdmin;
}
```

We can then call the function by using the `new` keyword by stating `user1 == function to create new user object` 

```Javascript
const user1 = new User("Josh", 28, true);
console.log(user1.name);
```

-------------------------------------------------------------------------------
[[Prototype Objects]]