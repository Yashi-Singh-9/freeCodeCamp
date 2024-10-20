# Fibonacci sequence

### Description

Write a function to generate the n<sup>th</sup> Fibonacci number.

The n<sup>th</sup> Fibonacci number is given by:

F<sub>n</sub> = F<sub>n-1</sub> + F<sub>n-2</sub>

The first two terms of the series are 0 and 1.

Hence, the series is: 0, 1, 1, 2, 3, 5, 8, 13...

---

### Tests

1. `fibonacci` should be a function.
2. `fibonacci(2)` should return a number.
3. `fibonacci(3)` should return 2.
4. `fibonacci(5)` should return 5.
5. `fibonacci(10)` should return 55.

### Solution

```javascript
function fibonacci(n) {
    // Base cases
    if (n === 0) return 0; // F(0) is 0
    if (n === 1) return 1; // F(1) is 1

    // Recursive case
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// Testing the function
console.log(fibonacci(2)); // Should return 1
console.log(fibonacci(3)); // Should return 2
console.log(fibonacci(5)); // Should return 5
console.log(fibonacci(10)); // Should return 55
```