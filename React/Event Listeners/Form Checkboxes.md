Checkboxes are a bit different then normal inputs in React. Below we have a sole checkbox which is an input that has a `checked` boolean property

In our `state` we added a property called `isFriendly` and set it to `true` and in our input we can set the checked property = to `formData.isFriendly`

The `name` property in the input needs to be set equal to the exact name we have in state which is `isFriendly` 

Also in our `handleChange` event we are deconstructing our values by calling `name, value, type, checked` and setting them = to `event.target` `const {name, value, type, checked} = event.target` 

```javascript
export default function Form() {
	const [formData, setFormData] = React.useState(
		{
			firstName: "",
			lastName: "",
			email: "",
			comments: "",
			isFriendly: true
		}
		
	)
	
	function handleChange(event) {
		const {name, value, type, checked} = event.target
		setFormData(prevFormData => {
			return {
				...prevFormData,
				[name]: type === "checkbox" ? checked : value
			}
		})
	}
	
	return (
		<form>
		<input
			type="checkbox"
			id="isFriendly"
			checked={formData.isFriendly}
			onChange={handleChange}
			name="isFriendly"
		/>
		
		<label htmlFor="isFriendly">Are you friendly?</label>
		<br />
		</form>
	)
}
```