Conditional rendering is a way in which we can render specific values if they exist and exclude values from the JSX if they DO NOT exist

```javascript

import React from "react"

export default function Joke(props) {
	return (
		<div>
			{props.setup && <h3>Setup: {props.setup}</h3>}
			<p>Punchline: {props.punchline}</p>
			<hr />
		</div>
	)
}
```

One thing we see here is that one of our lines has
`{props.setup && <h3>Setup: {props.setup}</h3>}`
This is basically saying IF `props.setup` is a truthy value then render everything on the right side of the `&&` operator.
IF it is a falsy value then do nothing.

----
 
# Ternary Operator in JSX

We can use Ternary operators directly inside of our JSX as seen below

In this instance we can check if `isGoingOut` is true or false inside our `<h1>` tag and if it is true we will display "Yes" if not we will display "No"

```javascript
export default function App() {

	const isGoingOut = false
	
	return (
		<div className="state">
			<h1 className="state--title">Do I feel like going out tonight?</h1>
			<div className="state--value">
				<h1>{isGoingOut ? "Yes" : "No"}</h1> 
			</div>
		</div>
	)

}
```

==A little trick== I found out is we can change a boolean value of state with 1 line of code. 

In our below example we have a function that checks if the div is clicked and changes the state value of `true` to `false` and if `false` it sets it to `true` 

This line of JS `setIsGoingOut(prevState => !prevState)`  basically changes the boolean to the opposite of what it originally was

```javascript
export default function App() {
	const [isGoingOut, setIsGoingOut] = React.useState(true)
	
	function changeMind() {
		setIsGoingOut(prevState => !prevState)
	}
	
	return (
		<div className="state">
			<h1 className="state--title">Do I feel like going out tonight?</h1>
			<div onClick={changeMind} className="state--value">
				<h1>{isGoingOut ? "Yes" : "No"}</h1>
			</div>
		</div>
	)
}
```