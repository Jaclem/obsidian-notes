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