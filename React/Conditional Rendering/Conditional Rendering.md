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

NOTE: A quick understanding on how this works, if the statement `props.setup` is truthy JavaScript continues looking at the rest of the code written and renders it. 
If however the statement is false JavaScript does not continue to interpret anything after the `&&` it actually stops interpretting before the `&&` 

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

We can use ternary's in more robust ways too like rendering multiple messages

In the below example we are seeing if the length of our messages array is equal to 0 and if so display the `<h1>` "You're all caught up!"

If not then we can render another message that says "You have __ unread message(s)"

```html
return (
	<div>
		{
			messages.length === 0 ?
			<h1>You're all caught up!</h1> :
			<h1>You have {messages.length} unread
			{messages.length > 1 ? "messages" : "message"}</h1>
		}
	</div>
)
```

We also have a ternary operator inside the last `<h1>` tag that checks if the length of messages is greater than 1 and if so it displays "messages" if not it displays "message"

