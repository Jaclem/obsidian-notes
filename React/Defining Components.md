Defining the componenet as a function is the modern way of using React.

This can be done using a regular function, arrow function, or inplicit return

```javascript
import React from 'react';

function App() {
  return <div className="App">Hello World!</div>;
}

// OR (arrow-function syntax)

const App = () => {
  return <div className="App">Hello World!</div>;
};

// OR (implicit return)

const App = () => <div className="App">Hello World!</div>;

export default App;
```

Unlike classbased components 
1.  We don’t have to import and extend “Component” from React.
2.  We don’t need a constructor.
3.  We don’t need the render function, instead we put the return statement right at the end of the function body.

When starting a new React app we should see something like this inside the `index.js` file

```javascript
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

In short, this line of code tells React to render the App component into the DOM, and more specifically, into the element with the id “root”.