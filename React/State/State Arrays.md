## Updating State Array

In React we have to go about updating our array differently then we would normally in JavaScript

In the below example our program is adding `Thing 3, etc.` when a button is clicked

How we do this is by targeting our previous value of state which is seen as `prevThingsArray` and using the `...` spread operator to spread in the existing array

This allows us to target everything that is already in the array

We then add a comma to denote that we're adding a new item to the array

```javascript
function App() {

	const [thingsArray, setThingsArray] = React.useState(["Thing 1", "Thing 2"])
	
	function addItem() {
		setThingsArray(prevThingsArray => {
			// ...prevThingsArray targets the existing elements while
			// `Thing ${prevThingsArray.length + 1}` adds a new item to the array 
			// while adding 1 to the length
			return [...prevThingsArray, `Thing ${prevThingsArray.length + 1}`]
		})
}
```

---
Another method we can use when changing the previous state of an array is using `.map()` on the previous state itself.

Below is a function in which we are trying to toggle a color change on some squares on the page and how we're accomplishing this is:

* We are calling the `setSquares` function and calling the previous array of squares `prevSquares` 
* Next we are returning the `prevSquares` and calling a `map` function for each square
* Then we are using a ternary operator to check if the `square.id` is `===` the `id` that's being passed to `toggle(id)` and if so then replace the squares object `{...square, on: !square.on` with a new object boolean value.
* Otherwise we are returning the original state of the square`: square` 
```javascript
export default function App() {

	const [squares, setSquares] = React.useState(boxes)
	
	function toggle(id) {
		setSquares(prevSquares => {
			return prevSquares.map((square) => {
				return square.id === id ? {...square, on: !square.on} : square
			})
		})
	}
```