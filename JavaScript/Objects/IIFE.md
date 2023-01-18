IIFE stands for ==Immediately Invoted Function Expression== is a function that runs as soon as it is defined.

The most popular use of this *type* of function is to avoid using global variables

Example: 
```javascript
const calculator = (() => {
  const add = (a, b) => a + b;
  const sub = (a, b) => a - b;
  const mul = (a, b) => a * b;
  const div = (a, b) => a / b;
  return {
    add,
    sub,
    mul,
    div,
  };
})();

calculator.add(3,5); // 8
calculator.sub(6,2); // 4
calculator.mul(14,5534); // 77476
```

