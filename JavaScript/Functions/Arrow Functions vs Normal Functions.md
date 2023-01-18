Arrow functions allow us to not only write code out quicker but they also act as a way to refer to `this` in an `object`

Here's an example of using a regular function in an object
```javascript
const objES5 = {
	name: 'Sam'
	print: function() {
		console.log(this.name)
		setTimeout(function () {
			console.log(this.name)
		}, 1000)
	}
}

objES5.print(); // undefined
```
Here is an example of using an arrow function in an object
```javascript
const objES6 = {
	name: 'Sam'
	print: function() {
		console.log(this.name)
		setTimeout(() => {
			console.log(this.name)
		}, 1000)
	}
}

objES6.print(); // Sam
```