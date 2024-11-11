# Vector cross product

### Description

A vector is defined as having three dimensions as being represented by an ordered collection of three numbers: (X, Y, Z).

---

Write a function that takes two vectors (arrays) as input and computes their cross product. Your function should return `null` on invalid inputs such as vectors of different lengths.

### Tests

1. `crossProduct` should be a function.
2. `crossProduct()` should return null.
3. `crossProduct([1, 2, 3], [4, 5, 6])` should return `[-3, 6, -3]`.

### Solution
```javascript
function crossProduct(A, B) {
  // Check if both vectors are arrays and have a length of 3
  if (!Array.isArray(A) || !Array.isArray(B) || A.length !== 3 || B.length !== 3) {
    return null; // Return null for invalid input
  }

  // Compute the cross product
  const crossProd = [
    A[1] * B[2] - A[2] * B[1],  // x-component
    A[2] * B[0] - A[0] * B[2],  // y-component
    A[0] * B[1] - A[1] * B[0]   // z-component
  ];

  return crossProd;
}

// Test cases
console.log(crossProduct([1, 2, 3], [4, 5, 6])); // Output: [-3, 6, -3]
console.log(crossProduct([1, 2], [4, 5, 6]));    // Output: null (invalid)
console.log(crossProduct([1, 2, 3], [4, 5]));    // Output: null (invalid)
console.log(crossProduct([1, 2, 3], 'not an array')); // Output: null (invalid)
```