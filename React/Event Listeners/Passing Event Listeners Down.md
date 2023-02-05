Passing event listeners for specific elements is tricky because we need to keep state at the highest level it can be, in the case we'll be looking at state is used in the `App` component.

In our app component below we can see that our state is being initiated here and we want to be able to click on the squares that are being created and figure out which square was clicked.

Each of our squares has an `id` so what we can do (because our `toggle` function takes a parameter of `id`) is in our `toggle` prop is throw in an arrow function that acts as its own individual function and give it an argument `square.id` which would be each unique id we want.

```javascript
export default function App() {
	const [squares, setSquares] = React.useState(boxes)
	
	function toggle(id) {
		console.log(id)
	}
	
	const squareElements = squares.map(square => (
		<Box
			key={square.id}
			{...square}
			toggle={() => toggle(square.id)} // This is the piece of code to 
			                                 // pay attention to
		/>
	))
	
	return (
		<main>
			{squareElements}
		</main>
	)
}
```

What we would have to do in this case is we would need a unique identifier to know which box is being clicked in order to handle our `onClick` function properly 

```javascript
export default function Box(props) {
	const styles = {
		backgroundColor: props.on ? "#222222" : "transparent"
	}
	
	return (
		<div
			style={styles}
			className="box"
			onClick={props.toggle}
		>	
		</div>
	)
}
```