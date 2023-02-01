```javascript
onClick 
onContextMenu 
onDoubleClick 
onDrag 
onDragEnd 
onDragEnter 
onDragExit
onDragLeave 
onDragOver 
onDragStart 
onDrop 
onMouseDown 
onMouseEnter 
onMouseLeave
onMouseMove 
onMouseOut 
onMouseOver 
onMouseUp
```

The way we can use one of these event listeners is by creating a function such as `handleClick()` and calling it by targeting the event listener in the JSX we would like to use

Seen below is two examples of this `onMouseOver={handleMouseOver}` and `onClick={handleClick}`

```javascript
export default function App() {

	function handleClick() {
		console.log("I was clicked!")
	}
	
	function handleMouseOver() {
		console.log("I was hovered")
	}

	return (
		<div className="container">
		<img src="https://picsum.photos/640/360" onMouseOver={handleMouseOver} />
		<button onClick={handleClick}>Click me</button>
		</div>
	)
}
```