useEffect is a hook in React that we can use to fetch APIs and update state without causing infinite loops. If you try and fetch an API and add the contents to state it will cause an infinite loop in the background of your program.

With useEffect we can avoid this. Below is an easy example of how useEffect works and why we would use it. 

In our app below we are setting the count + 1 every time the user clicks the button

In our useEffect function we are console.logging "Effect function ran". This function will only run on the first render of the page and any subsequent times the count is updated.

This is due to `[count]` which is an array dependency being added at the end of our useEffect function which tells the function not to run unless you notice a difference in the previous state and the new state.

```javascript
export default function App() {
	const [starWarsData, setStarWarsData] = React.useState({})
	const [count, setCount] = React.useState(0)

	React.useEffect(() => {
		console.log("Effect function ran")
	}, [count])
	
	return (
		<div>
			<pre>{JSON.stringify(starWarsData, null, 2)}</pre>
			<h2>The count is {count}</h2>
			<button onClick={() => setCount(prevCount => prevCount + 1)}>Add</button>
		</div>
	)
}
```

1. What is a "side effect" in React? What are some examples?
- Any code that affects an outside system.
- local storage, API, websockets, two states to keep in sync

2. What is NOT a "side effect" in React? Examples?
- Anything that React is in charge of.
- Maintaining state, keeping the UI in sync with the data, 
  render DOM elements

3. When does React run your useEffect function? When does it NOT run
   the effect function?
- As soon as the component loads (first render)
- On every re-render of the component (assuming no dependencies array)
- Will NOT run the effect when the values of the dependencies in the
  array stay the same between renders

4. How would you explain what the "dependecies array" is?
- Second paramter to the useEffect function
- A way for React to know whether it should re-run the effect function

In the example below we are fetching data from the Star Wars API, notice however that we do not have anything inside of the dependencies array `[]` at the end of our `useEffect` function. 

This is because we have no reason to grab this information more than once, we are setting the array with nothing inside because when the app component runs for the first time we want it to fetch the API but after that we do not want it to run again.

If we negate the blank `[]` we will cause an infinite loop.

```javascript
export default function App() {
	const [starWarsData, setStarWarsData] = React.useState({})
	const [count, setCount] = React.useState(0)
	
	React.useEffect(function() {
		console.log("Effect ran")
		fetch("https://swapi.dev/api/people/1")
			.then(res => res.json())
			.then(data => setStarWarsData(data))
	}, [])
	
	return (
		<div>
			<pre>{JSON.stringify(starWarsData, null, 2)}</pre>
			<h2>The count is {count}</h2>
			<button onClick={() => setCount(prevCount => prevCount + 1)}>Add</button>
		</div>
	)
}
```