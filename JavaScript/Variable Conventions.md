When there is a constant variable that is hard coded in like seen below the variable names can be named in **ALL_CAPITAL_LETTERS** 

```javascript
const COLOR_RED = "#F00"; 
const COLOR_GREEN = "#0F0"; 
const COLOR_BLUE = "#00F"; 
const COLOR_ORANGE = "#FF7F00";  // ...when we need to pick a color 
```

However if there is a constant variable that is not known it can be named with normal camelCasing convention such as 

```javascript
const pageLoadTime = /* time taken by a webpage to load */;
```

*(From javascript.info)*
The value of `pageLoadTime` is not known prior to the page load, so it’s named normally. But it’s still a constant because it doesn’t change after assignment.

*Some tips on naming conventions below:*
-   Use human-readable names like `userName` or `shoppingCart`.
-   Stay away from abbreviations or short names like `a`, `b`, `c`, unless you really know what you’re doing.
-   Make names maximally descriptive and concise. Examples of bad names are `data` and `value`. Such names say nothing. It’s only okay to use them if the context of the code makes it exceptionally obvious which data or value the variable is referencing.
-   Agree on terms within your team and in your own mind. If a site visitor is called a “user” then we should name related variables `currentUser` or `newUser` instead of `currentVisitor` or `newManInTown`.