The **`export`** declaration is used to export values from a JavaScript module. Exported values can then be imported into other programs with the `import` declaration

We can label any declaration as exported by placing `export` before it, be it a variable, function or a class.

For instance, here all exports are valid:

```javascript
// export an array 
export let months = ['Jan', 'Feb', 'Mar','Apr', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];

 // export a constant 
export const MODULES_BECAME_STANDARD_YEAR = 2015;  

// export a class 
export class User {   
	constructor(name) {     
		this.name = name;   
	} 
} // no ; at the end_

// Most JavaScript style guides don’t recommend semicolons after function and class declarations.

// That’s why there’s no need for a semicolon at the end of `export class` and `export function`:
```
 
## Export apart from declarations

Also, we can put `export` separately.

Here we first declare, and then export:

```javascript
// 📁 say.js 
function sayHi(user) {   
	alert(`Hello, ${user}!`); 
}  

function sayBye(user) {   
	alert(`Bye, ${user}!`); 
}  

export {sayHi, sayBye}; // a list of exported variables
```

## Export “as”

Let’s export functions as `hi` and `bye`:

```javascript
// 📁 say.js 
... 
export {sayHi as hi, sayBye as bye};
```

Now `hi` and `bye` are official names for outsiders, to be used in imports:

```javascript
// 📁 main.js 
import * as say from './say.js';  
say._hi_('John'); // Hello, John! 
say._bye_('John'); // Bye, John!
```

## Export Default

Mostly, modules that declare a single entity, e.g. a module `user.js` exports only `class User`.
This is preferred, so that every “thing” resides in its own module

Modules provide a special `export default` (“the default export”) syntax to make the “one thing per module” way look better.
```javascript
// 📁 user.js 
export default class User { // just add "default" 
	constructor(name) { 
		this.name = name; 
	} 
}
```

### There may be only one `export default` per file.

We can then [[import]] it without curly braces:
```javascript
// 📁 main.js 
import User from './user.js'; // not {User}, just User  

new User('John');
```

