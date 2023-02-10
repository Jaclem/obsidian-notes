Promises are a way to tell our code to wait until data is done fetching to continue.

Below we can see a promise in action `.then()` is a promise that is waiting for the data before assigning the value to our `pieceOfData` variable

```javascript
const myData = getData() // if this is refactored to return a Promise...

myData.then((data) => { // .then() tells it to wait until the promise is resolved
  const pieceOfData = data['whatever'] // and THEN run the function inside
})
```