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

