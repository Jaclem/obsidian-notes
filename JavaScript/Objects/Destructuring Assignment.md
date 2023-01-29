_Destructuring assignment_ is a special syntax that allows us to “unpack” arrays or objects into a bunch of variables, as sometimes that’s more convenient.

```javascript
const person = {
	img: "./images/mr-whiskerson.png",
	name: "Mr. Whiskerson",
	phone: "(800) 555-1234",
	email: "mr.whiskaz@catnap.meow"
}

  
// below we are declaring two new variables img, and name 
// when we console.log(name) below we will be able to get the name of the object above
// as it is destructuring the object

const {img, name} = person

console.log(name) // Mr. Whiskerson
```

Below is a cheet sheet for array destructuring that is also very helpful 

![[Pasted image 20230129125518.png]]