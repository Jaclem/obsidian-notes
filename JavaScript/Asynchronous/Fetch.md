Fetch allows us to put in an API url to fetch the data we want.

`.then()` takes a function (mainly an arrow function) and waits for the response before doing anything with the data `[IT'S A PROMISE]`

`.catch()` is also a promise but will handle any errors that occur when trying to grab the data.

```javascript
// URL (required), options (optional)
fetch('https://url.com/some/url')
  .then(function(response) {
    // Successful response :)
  })
  .catch(function(err) {
    // Error :(
  });
```

## Security
For security reasons, by default, browsers restrict HTTP requests to outside sources
We need to add the `mode: 'cors'` to allow us to actually make the HTTP request, if we do not then we will get an error.

```javascript
fetch('url.url.com/api', {
  mode: 'cors'
});
```

If we receive JSON data from an API that includes a promise we will need to use another `.then()` method to catch all the data thats kept inside the second promise as seen below

```javascript
fetch('http://example.com/movies.json', {mode: 'cors'})
  .then((response) => response.json())
  .then((data) => console.log(data));
```



