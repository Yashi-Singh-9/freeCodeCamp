# Accumulator factory

### Descrption

A problem posed by Paul Graham is that of creating a function that takes a single (numeric) argument and which returns another function that is an accumulator. The returned accumulator function in turn also takes a single numeric argument, and returns the sum of all the numeric values passed in so far to that accumulator (including the initial value passed when the accumulator was created).

--- 

Create a function that takes a number  n
  and generates accumulator functions that return the sum of every number ever passed to them.

Rules:

Do not use global variables.

Hint:

Closures save outer state.

---

### Tests

1. `accumulator` should be a function.
2. `accumulator(0)` should return a function.
3. `accumulator(0)(2)` should return a number.
4. Passing in the values 3, -4, 1.5, and 5 should return 5.5.

### Answer:

```javascript
function accumulator(n) {
  // Define a variable to keep track of the sum, initialized with the starting value
  let sum = n;

  // Return a new function that takes a single numeric argument and updates the sum
  return function(value) {
    sum += value; // Add the incoming value to the sum
    return sum;   // Return the updated sum
  };
}

// Example usage:
const acc = accumulator(0); // Create an accumulator with an initial value of 0
console.log(acc(3));  // Output: 3
console.log(acc(-4)); // Output: -1
console.log(acc(1.5)); // Output: 0.5
console.log(acc(5));  // Output: 5.5

```