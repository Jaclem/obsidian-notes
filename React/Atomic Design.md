**_Atoms:_**

Basic building blocks of matter, such as a button, input or a form label. They’re not useful on their own.

**_Molecules:_**

Grouping atoms together, such as combining a button, input and form label to build functionality.

**_Organisms:_**

Combining molecules together to form organisms that make up a distinct section of an interface (i.e. navigation bar)

**_Templates:_**

Consisting mostly of groups of organisms to form a page — where clients can see a final design in place.

**_Pages:_**

An ecosystem that views different template renders. We can create multiple ecosystems into a single environment — the application.

![[atomic-design.webp]]

Each component or service has its own isolated environment — everything needed to work on its own instance. You can see that each component **_/Buttons_** & **_/Form_** has its own set of styles, actions, and unit or integration tests that act like an independent piece of feature in your app. (_You can also add its own set of images and other local variables.)_ This makes it much easier, and reduces your efforts, to test your code consistently and effectively.

Note that if you define a new component inside **_/Delete, /Submit, /Login, or /Register_**, the nested component can only be used by its direct parent, and not its cousins.