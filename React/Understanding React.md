```javascript
import {StrictMode} from 'react';
import {createRoot} from 'react-dom/client';
import './styles.css';

import App from './App';
```

Lines 1-5 brings all the necessary pieces together:
-   React
-   React’s library to talk to web browsers (React DOM)
-   the styles for your components
-   the component you created in `App.js`.

We can add other divs inside a return by wrapping everything inside a fragment `<></>` like this (we're making a tic tac toe game)
```javascript
export default function Square() {

return (
	<>
		<div>
			<button className="square">1</button>
			<button className="square">2</button>
			<button className="square">3</button>
		</div>  
		
		<div>
			<button className="square">4</button>
			<button className="square">5</button>
			<button className="square">6</button>
		</div>
		
		<div>
			<button className="square">7</button>
			<button className="square">8</button>
			<button className="square">9</button>
		</div>
	</>
	)
}
```

# Properties (Props)

Creating a new component square we can use #Props to pass the value of each square from the parent component `Board()` to the child compoenent `Square()` 

Below we created a new component `Square()` that takes a prop `value` and we put the value inside the JSX button element 

Below that we changed the name of the default function from `square()` to `Board()` as it will be the game board. 
```javascript
function Square({ value }) {
	return <button className="square">{value}</button>
}
// we kept the same div elements but replacing the buttons with the <Square /> Component 
export default function Board() {
	return (
		<>
			<div className="board-row">
				<Square />
				<Square />
				<Square />
			</div>
			<div className="board-row">
				<Square />
				<Square />
				<Square />
			</div>
			<div className="board-row">
				<Square />
				<Square />
				<Square />
			</div>
		</>
	);
}
```

Inside the `Board()` component we can then update the value of each value we want added to the screen
![[Pasted image 20230122185419.png]]
Here's how it looks on the page
![[Pasted image 20230122185515.png]]

# Interactive Components

Now we can start to add some event handling to our page by using a function inside the `Square()` component. We create a new function `handleClick()` and when returning the button we also add the `onClick={ handleClick }` event handler that calls our function.

![[Pasted image 20230122191415.png]]

# State

React provides a special function called `useState` that you can call from your component to let it 
“*remember*” things.

When using State we need to import useState at the top of our file 
`import { useState } from 'react';` 

We can then get rid of our #Prop and add the state we're going to use 
`const [value, setValue] = useState(null);` 

![[Pasted image 20230122190514.png]]
We will also get rid of the value prop from all nine of the Square components 

![[Pasted image 20230122190926.png]]

## ==Important==!
```
value stores the value and setValue is a function that can be used to change the value.

The null passed to useState is used as the initial value for this state variable, so value here starts off equal to null.
```

Next we can add in our logic to use `setValue('X')` to set the value of the innerHTML when the button is clicked

![[Pasted image 20230122191132.png]]

# Lifting up state
[[Lifting up state]]
Lifting state into a is the processes of using state in the parent component instead of the child component (The parent component is the one that returns what you see on screen)

the best approach is to store the game’s state in the parent `Board` component instead of in each `Square`. The `Board` component can tell each `Square` what to display by passing a prop

**To collect data from multiple children, or to have two child components communicate with each other, declare the shared state in their parent component instead. The parent component can pass that state back down to the children via props.**

What we'll do is add the state to the `Board()` component with an array filled with 9 null statements

![[Pasted image 20230123085329.png]]

Next we need to pass the value prop down to each of the square components it renders

![[Pasted image 20230123085924.png]]

Next we'll be passing functionality FROM the `Board()` parent component to the `Square()` child component that handles clicks since we had to take out that funcitonality from the squares component

We are now giving our `<button>` element an `onClick` function of `onSquareClick`, then adding it as a deconstructed prop after `value` 

Next we add the function `handleClick` in the `Board()` component

Lastly we are are putting a prop inside of our `<Square />` component call as `onSquareClick={ handleClick }` What's happening here is we're telling the `Square()` component to call the `handleClick` function inside of Board and passing it back to `Square` 

![[Pasted image 20230123093205.png]]
to finish creating the clicking functionality in the `Board()` component we need to update a few things 

Firstly we need to pass in `i` into the handleClick function and `nextSquares[i] = 'X'` 
Next we'll need to add an arrow function that points to the function indicating which part of the array we're trying to update.

```javascript
function handleClick(i) {
	const nextSquares = squares.slice();
	nextSquares[i] = 'X';
	setSquares(nextSquares);
}

return (
	<>
		<div className="board-row">
			<Square value = {squares[0]} onSquareClick={() => handleClick(0)} />
		...
		</div>
	</>
)
```

the reason we need the arrow function inside the `{ }` is because without the arrow function we are not *Calling* the function we are passing it down as a prop and it gets run too quick and creates an infinite loop and causes errors.

With the arrow function it allows us to only call the `handleClick` function when the user actually clicks *instead of calling it immediately*

## In short we need if we're passing the prop to the Square component we need to pass the prop (which in this case is onSquareClick) and use an arrow function to allow the user to actually click on the item and have it do what we want

![[Pasted image 20230123103819.png]]
![[Pasted image 20230123103841.png]]
![[Pasted image 20230123103906.png]]

## Great explanation of what's going on in the above picture

Now that your state handling is in the `Board` component, the parent `Board` component passes props to the child `Square` components so that they can be displayed correctly. When clicking on a `Square`, the child `Square` component now asks the parent `Board` component to update the state of the board. When the `Board`’s state changes, both the `Board` component and every child `Square` component re-renders automatically. Keeping the state of all squares in the `Board` component will allow it to determine the winner in the future.

# Why Immutability is Important

There are generally two approaches to changing data. 

The first approach is to _mutate_ the data by directly changing the data’s values. The second approach is to replace the data with a new copy which has the desired changes. Here is what it would look like if you mutated the `squares` array:

```javascript
const squares = [null, null, null, null, null, null, null, null, null];
squares[0] = 'X';// Now `squares` is ["X", null, null, null, null, null, null, null, null];
```

And here is what it would look like if you changed data without mutating the `squares` array:

```javascript
const squares = [null, null, null, null, null, null, null, null, null];
const nextSquares = ['X', null, null, null, null, null, null, null, null];// Now `squares` is unchanged, but `nextSquares` first element is 'X' rather than `null`
```

Immutability makes complex features much easier to implement.

