
## [Getters and setters](https://javascript.info/property-accessors#getters-and-setters)

Accessor properties are represented by “getter” and “setter” methods. In an object literal they are denoted by `get` and `set`:

-   **`get`** – a function without arguments, that works when a property is read,
-   **`set`** – a function with one argument, that is called when the property is set,
-   **`enumerable`** – same as for data properties,
-   **`configurable`** – same as for data properties.

```javascript
let obj = { 
	get propName() { 
	// getter, the code executed on getting obj.propName 
	},
	
	set propName(value) { 
	// setter, the code executed on setting obj.propName = value 
	} 
};
```


```javascript

let user = { 
	name: "John", 
	surname: "Smith", 
	
	get fullName() { 
	return `${this.name} ${this.surname}`; 
	}, 
	
	set fullName(value) { 
	[this.name, this.surname] = value.split(" "); }
}; 
// set fullName is executed with the given value. 
user.fullName = "Alice Cooper"; 
alert(user.name); // Alice 
alert(user.surname); // Cooper
```

Getters/setters can be used as wrappers over “real” property values to gain more control over operations with them.

For instance, if we want to forbid too short names for `user`, we can have a setter `name` and keep the value in a separate property `_name`:

```javascript
let user = {
	get name() {
		return this._name;
	},

	set name(value) {
		if (value.length < 4) {
			alert("Name is too short, need at least 4 characters");
			return;	
		}
		this._name = value;
	}
};

user.name = "Pete"; 
alert(user.name); // Pete 

user.name = ""; // Name is too short...
```

There is a widely known convention that properties starting with an underscore `"_"` are internal and should not be touched from outside the object.