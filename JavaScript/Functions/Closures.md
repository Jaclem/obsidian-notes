Closures remember the outer function scope even after create time. This means that an inner function can hold onto the information given to an outer function until you call said function

*Definition:  Closure means that an inner function always has access to the variables and parameters of its outer function, even after the outer function has returned.*

Looking at the example below we are creating a variable and setting it == to our `human()`function with the argument `"Sina"`. 

We are then calling `sina.sayHi` and `sina.sayHowYouFeel` functions and these can be called whenever we want them to be called. ==This is closure.==

```javascript
function human(n) {
	const name = n;
	
	function sayHi() {
		console.log(`Hi I am ${name}`);
	}
	
	function sayHowYouFeel() {
		console.log(`${name} is feeling good!`);
	}

	return {
		sayHi,
		sayHowYouFeel
	}
}

const sina = human('Sina');
sina.sayHi(); // Hi I am Sina
sina.sayHowYouFeel(); // Sina is feeling good!
```