# Factors of an integer

### Description

Write a function that returns the factors of a positive integer as an array.

These factors are the positive integers by which the number being factored can be divided to yield a positive integer result.

---

### Tests

1. `factors` should be a function.
2. `factors(45)` should return `[1,3,5,9,15,45]`.
3. `factors(53)` should return `[1,53]`.
4. `factors(64)` should return `[1,2,4,8,16,32,64]`.

### Answer

```javascript
function factors(n) {
    // Return an array of factors of n
    const result = [];
    for (let i = 1; i <= n; i++) {
        if (n % i === 0) {
            result.push(i);
        }
    }
    return result;
}

// Test cases
console.log(factors(45)); // [1, 3, 5, 9, 15, 45]
console.log(factors(53)); // [1, 53]
console.log(factors(64)); // [1, 2, 4, 8, 16, 32, 64]
```