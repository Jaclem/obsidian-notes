In React we can actually save whole JSX elements as a signle variable like this

```javascript
const page = (
	<div>
		<h1 className="header">This is JSX</h1>
		<p>This is a paragraph</p>
	</div>
)

ReactDOM.render(
	page,
	document.getElementById("root")
)
```

We are then using ReactDOM.render() to render the variable and append it to the root div