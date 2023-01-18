```javascript
concat()
// Join several arrays into one

const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);

console.log(array3);
// expected output: Array ["a", "b", "c", "d", "e", "f"]
```

```javascript
indexOf()
// Returns the first position at which a given element appears in an array

const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

console.log(beasts.indexOf('bison'));
// expected output: 1

// start from index 2
console.log(beasts.indexOf('bison', 2));

```

```javascript
join()
// Combine elements of an array into a single string and return the string

const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join(''));
// expected output: "FireAirWater"
```

```javascript
pop()
// Removes the last element of an array

const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];

console.log(plants.pop());
// expected output: "tomato"
```

```javascript
push()
// Add a new element at the end

const animals = ['pigs', 'goats', 'sheep'];

const count = animals.push('cows');
// expected output: Array ["pigs", "goats", "sheep", "cows"]
```

```javascript
reverse()
// Reverse the order of the elements in an array

const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);
// expected output: "array1:" Array ["one", "two", "three"]

const reversed = array1.reverse();
console.log('reversed:', reversed);
// expected output: "reversed:" Array ["three", "two", "one"]
```

```javascript
shift()
// Remove the first element of an array

const array1 = [1, 2, 3];

const firstElement = array1.shift();

console.log(array1);
// expected output: Array [2, 3]
```

```javascript
slice()
// Pulls a copy of a portion of an array into a new array of 4 24

const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(2, -1));
// expected output: Array ["camel", "duck"]
```

```javascript
sort()
// Sorts elements alphabetically

const months = ['March', 'Jan', 'Feb', 'Dec'];
months.sort();
console.log(months);
// expected output: Array ["Dec", "Feb", "Jan", "March"]
```

```javascript
splice()
// Adds elements in a specified way and position

const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// inserts at index 1
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "June"]

months.splice(4, 1, 'May');
// replaces 1 element at index 4
```

```javascript
toString()
// Converts elements to strings

const array1 = [1, 2, 'a', '1a'];

console.log(array1.toString());
// expected output: "1,2,a,1a"
```

```javascript
unshift()
// Adds a new element to the beginning

const array1 = [1, 2, 3];

console.log(array1.unshift(4, 5));
// expected output: 5

console.log(array1);
// expected output: Array [4, 5, 1, 2, 3]
```

```javascript
valueOf()
// Returns the primitive value of the specified object
```

```javascript
reduce()
// the easiest-to-understand case for `reduce()` is to return the sum of all the elements in an array:

let arr = [1, 2, 3, 4, 5]; 
let result = arr.reduce((sum, current) => sum + current, 0); 
alert(result); // 15
```

The function passed to `reduce` uses only 2 arguments, that’s typically enough.

1.  On the first run, `sum` is the `initial` value (the last argument of `reduce`), equals `0`, and `current` is the first array element, equals `1`. So the function result is `1`.
2.  On the second run, `sum = 1`, we add the second array element (`2`) to it and return.
3.  On the 3rd run, `sum = 3` and we add one more element to it, and so on…

## Iterating through an array

we can use the of statement 
```javascript
    for(const i of scoreBoard){
      console.log([i]);
    }
```

### [Copy an array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#copy_an_array)

This example shows three ways to create a new array from the existing `fruits` array: first by using [spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax), then by using the [`from()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) method, and then by using the [`slice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice) method.

```Javascript
const fruits = ["Strawberry", "Mango"];

// Create a copy using spread syntax.
const fruitsCopy = [...fruits];
// ["Strawberry", "Mango"]

// Create a copy using the from() method.
const fruitsCopy2 = Array.from(fruits);
// ["Strawberry", "Mango"]

// Create a copy using the slice() method.
const fruitsCopy3 = fruits.slice();
// ["Strawberry", "Mango"]
```