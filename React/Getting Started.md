In the example below we can embed the result of calling the `formatName(user)` function into an `<h1>` element

```javascript
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!  
  </h1>
);
```

We can also embed `JSX` inside `if` statements and `for` loops like so:

```javascript
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;  
  }
  return <h1>Hello, Stranger.</h1>;}
```

We could use strings or JavaScript expressions as attributes as seen below

```javascript
const element = <a href="https://www.reactjs.org"> link </a>;

const element = <img src={user.avatarUrl}></img>;
```
Both of these do the same thing

JSX tags may contain children:

```javascript
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

Instead of having to use something like `const newElement = document.createElement('h1');` we can do this in React instead

```javascript
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```

# Function and Class Components

Creating components can be as easy as the function based component below

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

This can also be done in a class based component such as:

```javascript
class Welcome extends React.Component {
  render() { // When using class based components the render() function is a requirement
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```
This is the way a lot of companies still use react and is good to know

# Rendering a Component

We can also represent user-defined components such as

```javascript
function Welcome(props) {  // The welcome function takes a prop (property)
	return <h1>Hello, {props.name}</h1>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));
const element = <Welcome name="Sara" />; 
// The Welcome function is called and given an object name="Sara" or {name: 'Sara'}
root.render(element);
// root.render() injects the root div in index.html with the element we're calling as an argument
```

Compenents can also refer to other components in their output. For instance Welcome(props) is a component and App() is also a component

```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />      
      <Welcome name="Cahal" />      
      <Welcome name="Edite" />    
    </div>
  );
}
```

# Simplifying Components

A component like the one below works fine but we can simplify each section into it's own components that get added to the `comment` function

```javascript
function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
        <img className="Avatar"
          src={props.author.avatarUrl}
          alt={props.author.name}
        />
        <div className="UserInfo-name">
          {props.author.name}
        </div>
      </div>
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}
```

The comment component now has instances of other components inside of it that make it more readable and easier to use and modify.

Now `UserInfo` is its own component and can easily be added to the `comment` component

```javascript
function Comment(props) {
  return (
    <div className="Comment">
      <UserInfo user={props.author} />   
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}
```

# New Notes
https://beta.reactjs.org/learn#conditional-rendering
React components are JavaScript functions that return markup:

```javascript
function MyButton() {  
	return (    
		<button>I'm a button</button>  
	);
}
```

Now that you’ve declared `MyButton`, you can nest it into another component:

```javascript
export default function MyApp() {  
	return (    
		<div>      
			<h1>Welcome to my app</h1>      
			<MyButton />    
		</div>  
	);
}
```

We can use regular JavaScript in our file before our initial component so that we can easily add what we want to be rendered by the functionial component that is being exported

```javascript
const user = {
  name: 'Hedy Lamarr',
  imageUrl: 'https://i.imgur.com/yXOvdOSs.jpg',
  imageSize: 90,
};

export default function Profile() {
  return (
    <>
      <h1>{user.name}</h1>
      <img
        className="avatar"
        src={user.imageUrl}
        alt={'Photo of ' + user.name}
        style={{
          width: user.imageSize,
          height: user.imageSize
        }}
      />
    </>
  );
}
```

Here's an example of using an if statement to update the page with a certain component if the user is logged in or not

```javascript
let content;  

if (isLoggedIn) {  
	content = <AdminPanel />;  
} else {  
	content = <LoginForm />;  
}  

return (  
	<div>  
		{content}  
	</div>  
);
```

To add to this we can also use more complex pieces of logic and return a specific element that contains our new information 

In this example we're creating a new array with .map() and creating `<li>` tags to capture our `product.title` and then injecting them inside of a `<ul>` tag that is returning all `<li>` items

```javascript
const products = [  
	{ title: 'Cabbage', id: 1 },  
	{ title: 'Garlic', id: 2 },  
	{ title: 'Apple', id: 3 },  
];

const listItems = products.map(product =>  
	<li key={product.id}>  
		{product.title}  
	</li>  
);  

  
return (  
	<ul>{listItems}</ul>  
);
```

If we want to add styles to the element with JavaScript we can put it in `style={{}}` like seen below

```javascript
  style={{
	color: product.isFruit ? 'magenta' : 'darkgreen'
  }}
```

## Responding to events

You can respond to events by declaring _event handler_ functions inside your components:

```javascript
function MyButton() {  
	function handleClick() {    
	alert('You clicked me!');  
}  

return (    
	<button onClick={handleClick}>      
		Click me    
	</button>  
	);
}
```

# State

The state is a built-in React object that is used to contain data or information about the component.

The change in state can happen as a response to user action or system-generated events and these changes determine the behavior of the component and how it will render.

Often, we’ll want our component to “remember” some information and display it.

Below is a simple program to count the number of times a button is clicked.

```javascript
import { useState } from 'react';

function MyButton() {  
	const [count, setCount] = useState(0);
	
	function handleClick() {  
		setCount(count + 1);  
	}  
	

return (  
	<button onClick={handleClick}>  
		Clicked {count} times  
	</button>  
	);  
}
```

If you render the same component multiple times, each will get its own state. Try clicking each button separately:

```javascript
  return (
    <div>
      <h1>Counters that update separately</h1>
      <MyButton />
      <MyButton />
    </div>
  );
```

This translates to showing two different buttons and when one is clicked it shows:
Clicked 1 Times
Clicked 0 Times

# Hooks

Hooks are restricted functions that consist of a `use` keyword infront of the method. `useState` is a built-in Hook provided by React

Hooks can only be used at the highest level of your function. They must be the first thing you use.

# Props and passing information to other components

Let's say we wanted the same button we created earlier to update both buttons when either button is clicked 
For example if the button on top or bottom is clicked both buttons will display the count like so

Clicked 1 Times
Clicked 1 Times

```javascript
import { useState } from 'react';

export default function MyApp() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

// We put the count and the onClick function directly in the MyButton call
  return (
    <div>
      <h1>Counters that update together</h1>
      <MyButton count={count} onClick={handleClick} />
      <MyButton count={count} onClick={handleClick} />
    </div>
  );
}
// We are passing props to deconstructed Props to MyButton
function MyButton({ count, onClick }) {
  return (
    <button onClick={onClick}>
      Clicked {count} times
    </button>
  );
}
```
