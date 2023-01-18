The static **`import`** declaration is used to import read-only live bindings which are `exported` by another module.

## Import

Usually, we put a list of what to import in curly braces `import {...}`, like this:

```javascript
// 📁 main.js 
import {sayHi, sayBye} from './say.js';

sayHi('John'); // Hello, John! 
sayBye('John'); // Bye, John!
```

There is a lot to import, we can import everything as an object using `import * as <obj>`, for instance:
```javascript
// 📁 main.js 
import * as say from './say.js';

say.sayHi('John'); 
say.sayBye('John');
```

Something to note about importing everything as apposed to importing specific functions / objects / classes

1.  Explicitly listing what to import gives shorter names: `sayHi()` instead of `say.sayHi()`.
2.  Explicit list of imports gives better overview of the code structure: what is used and where. It makes code support and refactoring easier.

-------------------------------------------------------------------------------
## Import “as”

We can also use `as` to import under different names.

For instance, let’s import `sayHi` into the local variable `hi` for brevity, and import `sayBye` as `bye`:
```javascript
// 📁 main.js 
import {sayHi as hi, sayBye as bye} from './say.js';

hi('John'); // Hello, John! 
bye('John'); // Bye, John!
```

Usually, to keep the code consistent, there’s a rule that imported variables should correspond to file names, e.g:

```javascript
import User from './user.js';
import LoginForm from './loginForm.js'; 
import func from '/path/to/func.js'; 
...
```
