### [Factory Function Introduction](https://www.theodinproject.com/lessons/node-path-javascript-factory-functions-and-the-module-pattern#factory-function-introduction)

The factory function pattern is similar to constructors

However instead of using `new` to create an object, factory functions simply set up and return the new object when you call the function. Check out this example:

```javascript
const personFactory = (name, age) => {
  const sayHello = () => console.log('hello!');
  return { name, age, sayHello };
};

const jeff = personFactory('jeff', 27);

console.log(jeff.name); // 'jeff'

jeff.sayHello(); // calls the function and logs 'hello!'
```

With that knowledge in your pocket, check out this little hack:

```javascript
const name = "Maynard";
const color = "red";
const number = 34;
const food = "rice";

// logging all of these variables might be a useful thing to do,
// but doing it like this can be somewhat confusing.
console.log(name, color, number, food); // Maynard red 34 rice

// if you simply turn them into an object with brackets,
// the output is much easier to decipher:
console.log({name, color, number, food});
 // { name: 'Maynard', color: 'red', number: 34, food: 'rice' }
```

In the constructors lesson, we looked fairly deeply into the concept of prototypes and inheritance, or giving our objects access to the methods and properties of another object. There are a few easy ways to accomplish this while using factories. Check this one out:

```javascript
const Person = (name) => {
  const sayName = () => console.log(`my name is ${name}`);
  return {sayName};
}

const Nerd = (name) => {
  // simply create a person and pull out the sayName function with destructuring assignment syntax!
  const {sayName} = Person(name);
  const doSomethingNerdy = () => console.log('nerd stuff');
  return {sayName, doSomethingNerdy};
}

const jeff = Nerd('jeff');

jeff.sayName(); //my name is jeff
jeff.doSomethingNerdy(); // nerd stuff
```

There are a few easy ways to accomplish giving our objects access to the methods and properties of another object while using factories. Check this one out:

```javascript
const Person = (name) => {
  const sayName = () => console.log(`my name is ${name}`);
  return {sayName};
}

const Nerd = (name) => {
  // simply create a person and pull out the sayName function with destructuring assignment syntax!
  const {sayName} = Person(name);
  const doSomethingNerdy = () => console.log('nerd stuff');
  return {sayName, doSomethingNerdy};
}

const jeff = Nerd('jeff');

jeff.sayName(); //my name is jeff
jeff.doSomethingNerdy(); // nerd stuff
```