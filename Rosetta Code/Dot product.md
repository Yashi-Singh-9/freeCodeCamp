# Dot product

### Description

Create a function, to compute the dot product, also known as the scalar product of two vectors.

---

### Tests

1. `dotProduct` should be a function.
2. `dotProduct([1, 3, -5], [4, -2, -1])` should return a number.
3. `dotProduct([1, 3, -5], [4, -2, -1])` should return `3`.
4. `dotProduct([1, 2, 3, 4, 5], [6, 7, 8, 9, 10])` should return `130`.
5. `dotProduct([5, 4, 3, 2], [7, 8, 9, 6])` should return `106`.
6. `dotProduct([-5, 4, -3, 2], [-7, -8, 9, -6])` should return `-36`.
7. `dotProduct([17, 27, 34, 43, 15], [62, 73, 48, 95, 110])` should return `10392`.

### Answer:
```javascript
function dotProduct(vector1, vector2) {
  // Compute the dot product by multiplying corresponding elements and summing them up
  return vector1.reduce((sum, current, index) => sum + current * vector2[index], 0);
}

// Test cases
console.log(dotProduct([1, 3, -5], [4, -2, -1])); // Expected: 3
console.log(dotProduct([1, 2, 3, 4, 5], [6, 7, 8, 9, 10])); // Expected: 130
console.log(dotProduct([5, 4, 3, 2], [7, 8, 9, 6])); // Expected: 106
console.log(dotProduct([-5, 4, -3, 2], [-7, -8, 9, -6])); // Expected: -36
console.log(dotProduct([17, 27, 34, 43, 15], [62, 73, 48, 95, 110])); // Expected: 10392
```