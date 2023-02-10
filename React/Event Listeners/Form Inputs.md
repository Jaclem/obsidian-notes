To be able to handle multiple inputs data in a form what we can do as seen below is to set a state variable equal to an object and pass our `firstname: lastName:` properties inside of it equal to an empty string

Using our onChange event listener we can pass in the event to the `handleChange(event)` and target our state setter function to set the new form data.

In our setFormData function we are targeting our previous state `prevFormData` and returning an object.

Inside the object we are using the spread operator to keep the old object data intact `...prevFormData` 

Lastly we are using the `Computed Properties` feature in ES6 to allow us to target the event target name (which would be firstName or lastName) and set it equal to the targets value

```javascript
export default function Form() {

	const [formData, setFormData] = React.useState({
		firstName: '',
		lastName: ''
	})
	
	function handleChange(event) {
		const {name, value} = event.target
		setFormData(prevFormData => {
			return {
				...prevFormData, // note on this below
				[name]: value
			}
		})
	}
	
	return (
		<form>
			<input
			type="text"
			placeholder="First Name"
			name="firstName"
			onChange={handleChange}
			value={formData.firstName} // VERY IMPORTANT
		/>
	
		<input
			type="text"
			placeholder="Last Name"
			name="lastName"
			onChange={handleChange}
			value={formData.lastName} // VERY IMPORTANT
			/>
		</form>
	)
}
```

## Value inside Input
The above text explains how everything works but I wanted to take a second and talk about how important it is to add this piece of code to each input `value={formData.NAME}` 

This is called *Controlled Inputs* and is a big part of React on all levels but for this example setting the value equal to the state name that we associate that specific input to gives control to React instead of having each Input handling its own state

---
## Note:
The spread operator is used to spread in all of the key value pairs from the previous input.
Anything after that in `[name]` is overwriting the previous value with the new value for the state change based off of the name value of the input.

---
