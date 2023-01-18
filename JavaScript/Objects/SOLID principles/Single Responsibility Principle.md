==A  class, object, or module should only have one responsibility==. This doesn’t mean that an object can only do one thing, but it does mean that everything an object does should be part of one responsibility.

Most of our code has functions to update and write things to the DOM in addition to our application logic. It’s a _really_ good idea to separate your DOM stuff from the application logic.

Such as:
```javascript
function isGameOver() {

  // game over logic goes here!

  if (gameOver){
    DOMStuff.gameOver(this.winner);
  }
}
```

An object should have a cohesive set of behaviors, together comprising a single responsibility

Here is the structure for what objects should specifically do in a program, adding group behaviors into cohesive groups of responsibilities related to the object’s intended role.

-   ==**Information holder**== – an object designed to know certain information and provide that information to other objects.
-   **==Structurer==** – an object that maintains relationships between objects and information about those relationships.
-   **==Service provider==** – an object that performs specific work and offers services to others on demand.
-   **==Controller==** – an object designed to make decisions and control a complex task.
-   **==Coordinator==** – an object that doesn’t make many decisions but, in a rote or mechanical way, delegates work to other objects.
-   **Interfacer** – an object that transforms information or requests between distinct parts of a system.