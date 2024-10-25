# Largest int from concatenated ints

### Description

Given a set of positive integers, write a function to order the integers in such a way that the concatenation of the numbers forms the largest possible integer and return this integer.

### Tests

1. `maxCombine` should be a function.
2. `maxCombine([1, 3, 3, 4, 55])` should return a number.
3. `maxCombine([1, 3, 3, 4, 55])` should return `554331`.
4. `maxCombine([71, 45, 23, 4, 5])` should return `71545423`.
5. `maxCombine([14, 43, 53, 114, 55])` should return `55534314114`.
6. `maxCombine([1, 34, 3, 98, 9, 76, 45, 4])` should return `998764543431`.
7. `maxCombine([54, 546, 548, 60])` should return `6054854654`.

### Answer:

```javascript
function maxCombine(arr) {
    // Convert numbers to strings for concatenation
    const arrStr = arr.map(num => num.toString());
    
    // Sort the array based on custom logic
    arrStr.sort((a, b) => (b + a) - (a + b));
    
    // Join the sorted array into the largest number
    const result = arrStr.join('');
    
    // Edge case: If the result is just zeros, return 0
    return Number(result[0] === '0' ? '0' : result);
}

// Test cases
console.log(maxCombine([1, 3, 3, 4, 55])); // 554331
console.log(maxCombine([71, 45, 23, 4, 5])); // 71545423
console.log(maxCombine([14, 43, 53, 114, 55])); // 55534314114
console.log(maxCombine([1, 34, 3, 98, 9, 76, 45, 4])); // 998764543431
console.log(maxCombine([54, 546, 548, 60])); // 6054854654
```