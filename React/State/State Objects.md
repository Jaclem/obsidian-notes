## Updating State Object

In the below example we have a stateful object called `contact` and a boolean value inside called `isFavorite` set to true

in order for us to change this value *(in our case if a button is clicked)* is to use our `setContact` function and target the previous state of state using `prevContact` and return an object

Here what we're doing is using a spread operator to get all the contents of the object that are **NOT** going to change and then targeting the one object that is changing I.E `isFavorite` and telling the object that we want the opposite of what the boolean value currently is when clicking on it.

```javascript
export default function App() {

	const [contact, setContact] = React.useState({
		firstName: "John",
		lastName: "Doe",
		phone: "+1 (719) 555-1212",
		email: "itsmyrealname@example.com",
		isFavorite: false
	})
	
	let starIcon = contact.isFavorite ? "star-filled.png" : "star-empty.png"
	
	function toggleFavorite() {

		setContact(prevContact => {
			return {
				...prevContact,
				isFavorite: !prevContact.isFavorite
			}
		})
	}
}
```

---
