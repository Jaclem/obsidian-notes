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
				<h1>{test}</h1>
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

==Important Note==
If you do not care about the previous value in state such as if `React.useState("")` has an empty string like it does in this example we can update state directly by just calling `setTest("New Value")` without using the `prevCount` syntax

---
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
## Updating State Object

In the below example we have a stateful object called `contact` and a boolean value inside called `isFavorite` set to true

in order for us to change this value *(in our case if a button is clicked)* is to use our `setContact` function and target the previous state of state using `prevContact` and return an object

Here what we're doing is using a spread operator to get all the contents of the object that are **NOT** going to change and then targeting the one object that is changing I.E `isFavorite` and telling the object that we want the opposite of what the boolean value currently is when clicking on it.

```javascript
export default function App() {

	const [contact, setContact] = React.useState({
		firstName: "John",
		lastName: "Doe",
		phone: "+1 (719) 555-1212",
		email: "itsmyrealname@example.com",
		isFavorite: false
	})
	
	let starIcon = contact.isFavorite ? "star-filled.png" : "star-empty.png"
	
	function toggleFavorite() {

		setContact(prevContact => {
			return {
				...prevContact,
				isFavorite: !prevContact.isFavorite
			}
		})
	}
}
```