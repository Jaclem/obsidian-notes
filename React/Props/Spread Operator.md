One other very important part of this is the `spread operator` as seen below.

A lot of times real React developers will use the spread syntax to bring in their Object

```javascript 
export default function App() {
	const parsedData = data.map((info) => {
		return <Card
			key={item.id}
			{...item} // This is the spread syntax
		/>
	})

	return (
		{parsedData}
	)
}

```

## What this does:
In this case the spread operator takes the `properties` of the `data`, and creates a separate prop for each different data type.

## Important Note!
When the spread operator is used the props in the component do NOT need to be called in the same way as `props.item.OBJECT-NAME` instead we can use the traditional way of calling props
Such as:
`props.OBJECT-NAME`