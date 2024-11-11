# Vector dot product

### Description

A vector can have one or more values represented by an ordered collection. Examples could be (x), (x, y), or (x, y, z).

---

Write a function that takes two vectors (represented as one-dimensional arrays) as input and computes their dot product. Your function should return `null` on invalid inputs such as vectors of different lengths or passing anything other than two vectors.

### Tests

1. `dotProduct` should be a function.
2. `dotProduct()` should return `null`.
3. `dotProduct([1], [1])` should return `1`.
4. `dotProduct([1], [1, 2])` should return `null`.
5. `dotProduct([1, 3, -5], [4, -2, -1])` should return `3`.
6. `dotProduct([3, 2, 1], [2, 4, 2], [5, 3, 1])` should return `null`.
7. `dotProduct([ 0, 3, 6, 9, 12 ], [ 0, 4, 8, 12, 16 ])` should return `360`.

### Solution

```javascript
function dotProduct(vector1, vector2) {
    // Check if there are exactly two input arrays
    if (arguments.length !== 2) {
        return null;
    }

    // Check if both inputs are arrays
    if (!Array.isArray(vector1) || !Array.isArray(vector2)) {
        return null;
    }

    // Check if both vectors have the same length
    if (vector1.length !== vector2.length) {
        return null;
    }

    // Compute the dot product
    let result = 0;
    for (let i = 0; i < vector1.length; i++) {
        result += vector1[i] * vector2[i];
    }

    return result;
}
```