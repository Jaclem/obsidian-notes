In react in order to push items to an array we need to use the spreak syntax to let the state know that we want the current items in the array then we can push the newest item into the array.

```javascript
import {useState} from 'react';

export default function App() {
  const [names, setNames] = useState(['Alice', 'Bob']);

  const handleClick = () => {
    // 👇️ push to end of the state array
    setNames(current => [...current, 'Carl']);

    // 👇️ spread an array into the state array
    // setNames(current => [...current, ...['Carl', 'Delilah']]);

    // 👇️ push to the beginning of the state array
    // setNames(current => ['Zoey', ...current]);
  };

  return (
    <div>
      <div>
        <button onClick={handleClick}>
          Push to state array
        </button>
      </div>

      {names.map((element, index) => {
        return (
          <div key={index}>
            <h2>{element}</h2>
          </div>
        );
      })}
    </div>
  );
}
```

-------------------------------------------------------------------------------
We can also accomplish something similar by using regular JavaScript outisde of our return.

What we're doing here is creating a new element `jokeElements` that is using the `.map()` method and returning our `<Joke />` component with a few props

The props are `joke.setup` and `joke.punchline` which is directly referencing data that is stored in our `jokesData` file

```javascript
import React from "react"
import Joke from "./Joke"
import jokesData from "./jokesData"

export default function App() {

	const jokeElements = jokesData.map(joke => {
		return <Joke setup={joke.setup} punchline={joke.punchline} />
})

	return (
		<div>
			{jokeElements}
		</div>
	)
}
```

We can access the data and use it as props just like any other object by using . notation

The data file looks like this

```javascript
export default [
	{
		setup: "I got my daughter a fridge for her birthday.",
		punchline: "I can't wait to see her face light up when she opens it."
	},

	{
		setup: "How did the hacker escape the police?",
		punchline: "He just ransomware!"
	},
	
	{
		setup: "Why don't pirates travel on mountain roads?",
		punchline: "Scurvy."
	},

	{
		setup: "Why do bees stay in the hive in the winter?",
		punchline: "Swarm."
	},
	
	{
		setup: "What's the best thing about Switzerland?",
		punchline: "I don't know, but the flag is a big plus!"
	}
]
```

This data gives us an idea of what we're doing when we're using . notation trying to map this data as props.

-------------------------------------------------------------------------------

We can also map it out using a nested return for example:

```javascript 
const parsedData = data.map((info) => {
	return <Card
		img={info.coverImg}
		rating={info.stats.rating}
		reviewCount={info.stats.reviewCount}
		location={info.location}
		title={info.title}
		price={info.price}
	/>
})
```

As we can see our `<Card` props are getting a bit out of control, to fix this we can pass just the `item` object to get all the information as props that we need [[Passing Object as Prop]]

