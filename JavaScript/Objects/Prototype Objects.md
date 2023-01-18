# Prototype

All objects in JavaScript have a `prototype`. Stated simply, the prototype is another object that the original object _inherits_ from, which is to say, the original object has access to all of its prototype’s methods and properties.

```javascript
function Student(name, grade) {
  this.name = name
  this.grade = grade
}

Student.prototype.sayName = function() {
  console.log(this.name)
}
Student.prototype.goToProm = function() {
  console.log("Eh.. go to prom?")
}
```

If you’re using constructors to make your objects it is best to define functions on the `prototype` of that object. 

Doing so means that a single instance of each function will be shared between all of the Student objects. 

If we declare the function directly in the constructor, that function would be duplicated every time a new Student is created. 

In a project that is creating thousands of objects, it really can make a difference.

-------------------------------------------------------------------------------------------------------------
### Prototype Attribute of Objects Created With a Constructor Function 
Objects created with the new keyword and any constructor other than the Object () constructor, get their prototype from the constructor function.

For Example:

```javascript
function Account () {

}
var userAccount = new Account () 
// userAccount initialized with the Account () constructor and as such its prototype attribute (or prototype object) is Account.prototype.
```

**Demonstration of inheritiance in JavaScript** 

```javascript
function Plant () {
this.country = "Mexico";
this.isOrganic = true;
}

// Add the showNameAndColor method to the Plant prototype property
Plant.prototype.showNameAndColor =  function () {
	console.log("I am a " + this.name + " and my color is " + this.color);
}

// Add the amIOrganic method to the Plant prototype property
Plant.prototype.amIOrganic = function () {
	if (this.isOrganic)
	console.log("I am organic, Baby!");
}
```

-------------------------------------------------------------------------------
### Object.create()

The **`Object.create()`** method creates a new object, using an existing object as the prototype of the newly created object.

```javascript
const person = {
  isHuman: false,
  printIntroduction: function() {
    console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
  }
};

const me = Object.create(person);

me.name = 'Matthew'; // "name" is a property set on "me", but not on "person"
me.isHuman = true; // inherited properties can be overwritten

me.printIntroduction();
// expected output: "My name is Matthew. Am I human? true"
```