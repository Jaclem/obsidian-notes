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