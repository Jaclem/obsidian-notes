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
