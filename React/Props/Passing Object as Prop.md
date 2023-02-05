As we can see below our `<Card` props are getting a bit out of control, to fix this we can pass just the `item` object to grab all the information and use it in our component as needed

```javascript
export default function App() {
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

	return (
		{parsedData}
	)
}

```

The way we can do this is by removing all props and creating a prop called `item={item}`

```javascript 
const parsedData = data.map((info) => {
	return <Card
		key={info.id}
		item={item}
	/>
})
```

`item={item}` can also be referred to as `{...item}` if this is the case please see [[Spread Operator]]

```javascript 
const parsedData = data.map((info) => {
	return <Card
		key={info.id}
		{...item}
	/>
})
```

Now in our *Actual* component we can target `props.item.OBJECT-NAME`.

We are now targeting the actual object in our component such as item.prop.location

If we `console.log(item)` we would see all of the objects and their names and this can help us figure out what to call them on the component itself.

```javascript
return (
	<div className="card--stats">
		<img src="../images/star.png" className="card--star" />
		<span>{props.item.stats.rating}</span>
		<span className="gray">({props.item.stats.reviewCount}) • </span>
		<span className="gray">{props.item.location}</span>
		</div>
		<p className="card--title">{props.item.title}</p>
	</div>
)
```

-------------------------------------------------------------------------------


