Let's say we want to add some styling to our components and want them to be dynamic such as if dark mode is turned on.

Below we are then creating a new variable called `styles` and setting it `=` to an object that takes the backgroundColor object and sets it equal to our ternary operator value

The ternary operator is there to determine **if true use color `#222222` if false use `#cccccc`** 

```javascript
export default function App(props) {
	const [squares, setSquares] = React.useState(boxes)

	const styles = {
		backgroundColor: props.darkMode ? "#222222" : "#cccccc"
	}
	
	const squareElements = squares.map(square => (
		<div style={styles} className="box" key={square.id}></div>
	))
	
	return (
		<main>
			{squareElements}
		</main>
	)
}
```
