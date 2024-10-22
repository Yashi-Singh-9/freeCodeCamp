# FizzBuzz

### Description

Write a program that generates an array of integers from 1 to 100 (inclusive). But:

- for multiples of 3, add `"Fizz"` to the array instead of the number
- for multiples of 5, add `"Buzz"` to the array instead of the number
- for multiples of 3 and 5, add `"FizzBuzz"` to the array instead of the number

---

Your program should return an array containing the results based on the rules above.

### Tests

1. `fizzBuzz` should be a function.
2. `fizzBuzz()` should return an Array.
3. Numbers divisible by only 3 should return `"Fizz"`.
4. Numbers divisible by only 5 should return `"Buzz"`.
5. Numbers divisible by both 3 and 5 should return `"FizzBuzz"`.
6. Numbers not divisible by either 3 or 5 should return the number itself.

### Answer:

```javascript
function fizzBuzz() {
  // Initialize an empty array to store the results
  const result = [];

  // Loop through numbers from 1 to 100
  for (let i = 1; i <= 100; i++) {
    // Check if number is divisible by both 3 and 5
    if (i % 3 === 0 && i % 5 === 0) {
      result.push("FizzBuzz");
    }
    // Check if number is divisible by only 3
    else if (i % 3 === 0) {
      result.push("Fizz");
    }
    // Check if number is divisible by only 5
    else if (i % 5 === 0) {
      result.push("Buzz");
    }
    // If not divisible by 3 or 5, push the number itself
    else {
      result.push(i);
    }
  }

  // Return the resulting array
  return result;
}

// Call the fizzBuzz function to test
console.log(fizzBuzz());
```