useState is the main way we can save data in React so that when our component re-renders the *state* will stay the same.

The way we can do this is by creating a variable = `React.useState()` or just `useState()` 

The reason for the `[]` after calling the variable is that useState is actually an array with a function inside of it and the brackets `[]` are destructuring the information inside of the array making it more simple to use in the component.

useState looks like this when logging it `["Yes", f()]` 

```javascript
export default function App() {
	const [test, setTest] = React.useState("Yes")

	return (
		<div className="state">
			<h1 className="state--title">Is state important to know?</h1>
			<div className="state--value">
				<h1>{isImportant}</h1>
			</div>
		</div>
	)
}
```

-----------------------------

## Updating State

The best practice way of updating state is to use a function to target the previous value of state to update it to the new value of state

In the case below `count` is set to `0` and when we update it in our `add()` function we are using `setCount(prevcount => prevCount + 1` 

What this does is sets the previous value to the same value + 1

```javascript
export default function App() {

const [count, setCount] = React.useState(0)

	/**
	* Note: if you ever need the old value of state
	* to help you determine the new value of state,
	* you should pass a callback function to your
	* state setter function instead of using
	* state directly. This callback function will
	* receive the old value of state as its parameter,
	* which you can then use to determine your new
	* value of state.
	*/

	function add() {
		setCount(prevCount => prevCount + 1)
	}

	// Another way we can view this is by using function() as seen below
	function add() {
		setCount(function(prevCount) {
			return prevCount + 1
		})
	}
```

Another way to understand this in case we're having a hard time is to set the `prevCount` to `currentVal` to let us know that we are updating the **Current Value** of state.

