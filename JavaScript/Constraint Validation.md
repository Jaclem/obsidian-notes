https://www.w3schools.com/js/js_validation_api.asp

Validating forms / other items in JavaScript with a single method.

We can use the `checkValidity()` method in JS to return true if an input element contains valid data

and `setCustomValidity()` which sets the validationMessage property of an input element


```html
<input id="id1" type="number" min="100" max="300" required>  
<button onclick="myFunction()">OK</button>  
  
<p id="demo"></p>  
```

```javascript

function myFunction() {
  const inpObj = document.getElementById("id1");
  if (!inpObj.checkValidity()) {
    document.getElementById("demo").innerHTML = inpObj.validationMessage;
  } else {
    document.getElementById("demo").innerHTML = "Input OK";
  } 
} 
```
