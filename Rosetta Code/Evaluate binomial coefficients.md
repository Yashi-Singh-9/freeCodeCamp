# Evaluate binomial coefficients

### Description

Write a function to calculate the binomial coefficient for the given value of n and k.

This formula is recommended:

![](Images/binomial.png)

### Tests

1. `binom` should be a function.
2. `binom(5,3)` should return 10.
3. `binom(7,2)` should return 21.
4. `binom(10,4)` should return 210.
5. `binom(6,1)` should return 6.
6. `binom(12,8)` should return 495.

### Answer:

```javascript
function binom(n, k) {
    if (k === 0 || k === n) {
        return 1;
    }
    if (k > n) {
        return 0;
    }
    let result = 1;
    for (let i = 1; i <= k; i++) {
        result = result * (n - i + 1) / i;
    }
    return result;
}

// Test cases
console.log(binom(5, 3));  // Should return 10
console.log(binom(7, 2));  // Should return 21
console.log(binom(10, 4)); // Should return 210
console.log(binom(6, 1));  // Should return 6
console.log(binom(12, 8)); // Should return 495
```