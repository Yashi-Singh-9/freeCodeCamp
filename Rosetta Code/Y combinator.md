# Y combinator

### Description

In strict [functional programming](https://www.freecodecamp.org/news/the-principles-of-functional-programming/) and the lambda calculus, functions (lambda expressions) don't have state and are only allowed to refer to arguments of enclosing functions. This rules out the usual definition of a recursive function wherein a function is associated with the state of a variable and this variable's state is used in the body of the function.

The Y combinator is itself a stateless function that, when applied to another stateless function, returns a recursive version of the function. The Y combinator is the simplest of the class of such functions, called fixed-point combinators.

---

Define the stateless Y combinator function and use it to compute the factorials. The `factorial(N)` function is already given to you.

### Tests

1. Y should return a function.
2. factorial(1) should return 1.
3. factorial(2) should return 2.
4. factorial(3) should return 6.
5. factorial(4) should return 24.
6. factorial(10) should return 3628800.

### Solution

```javascript
// Y Combinator definition
const Y = (F) => {
  return (x => F(v => x(x)(v)))((x) => F(v => x(x)(v)));
};

// Factorial function using the Y combinator
const factorial = Y((f) => (n) => (n === 0 ? 1 : n * f(n - 1)));

// Testing the factorial function
console.log(factorial(1)); // 1
console.log(factorial(2)); // 2
console.log(factorial(3)); // 6
console.log(factorial(4)); // 24
console.log(factorial(10)); // 3628800
```