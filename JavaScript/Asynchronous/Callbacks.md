In essence a callback is a function that is provided as a perameter to our other methods and is invoked at a certain point in time

> A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action. [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function)

Callbacks are simply functions that get passed into other functions. For example:

```javascript
myDiv.addEventListener("click", function(){
  // do something!
})
```

Here, the function `addEventListener()` takes a callback (the “do something” function) and then calls it when `myDiv` gets clicked.