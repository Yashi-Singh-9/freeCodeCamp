# Sum multiples of 3 and 5

### Description 

The objective is to write a function that finds the sum of all positive multiples of 3 or 5 below n.

### Tests

1. `sumMults` should be a function.
2. `sumMults(10)` should return a number.
3. `sumMults(10)` should return `23`.
4. `sumMults(100)` should return `2318`.
5. `sumMults(1000)` should return `233168`.
6. `sumMults(10000)` should return `23331668`.
7. `sumMults(100000)` should return `2333316668`.

### Solution:

```javascript
function sumMults(n) {
  let sum = 0;
  for (let i = 0; i < n; i++) {
    if (i % 3 === 0 || i % 5 === 0) {
      sum += i;
    }
  }
  return sum;
}

// Test cases
console.log(sumMults(10)); // Should return 23
console.log(sumMults(100)); // Should return 2318
console.log(sumMults(1000)); // Should return 233168
console.log(sumMults(10000)); // Should return 23331668
console.log(sumMults(100000)); // Should return 2333316668
```