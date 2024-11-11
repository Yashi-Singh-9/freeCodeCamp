# Sum of squares

### Description

Write a function to find the sum of squares of an array of integers.

### Tests

1. `sumsq` should be a function.
2. `sumsq([1, 2, 3, 4, 5])` should return a number.
3. `sumsq([1, 2, 3, 4, 5])` should return `55`.
4. `sumsq([25, 32, 12, 7, 20])` should return `2242`.
5. `sumsq([38, 45, 35, 8, 13])` should return `4927`.
6. `sumsq([43, 36, 20, 34, 24])` should return `5277`.
7. `sumsq([12, 33, 26, 18, 1, 16, 3])` should return `2499`.

### Solution

```javascript
function sumsq(arr) {
    return arr.reduce((sum, num) => sum + num * num, 0);
}

// Testing the function
console.log(sumsq([1, 2, 3, 4, 5])); // 55
console.log(sumsq([25, 32, 12, 7, 20])); // 2242
console.log(sumsq([38, 45, 35, 8, 13])); // 4927
console.log(sumsq([43, 36, 20, 34, 24])); // 5277
console.log(sumsq([12, 33, 26, 18, 1, 16, 3])); // 2499
```