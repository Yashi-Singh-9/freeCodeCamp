# Spiral matrix

#### Description

Produce a spiral array. A *spiral array* is a square arrangement of the first N<sup>2</sup> natural numbers, where the numbers increase sequentially as you go around the edges of the array spiraling inwards. For example, given 5, produce this array:
```
0  1  2  3  4
15 16 17 18 5
14 23 24 19 6
13 22 21 20 7
12 11 10  9 8
```

### Tests

1. `spiralArray` should be a function.
2. `spiralArray(3)` should return an array.
3. `spiralArray(3)` should return `[[0, 1, 2],[7, 8, 3],[6, 5, 4]]`.
4. `spiralArray(4)` should return `[[0, 1, 2, 3],[11, 12, 13, 4],[10, 15, 14, 5],[9, 8, 7, 6]]`.
5. `spiralArray(5)` should return `[[0, 1, 2, 3, 4],[15, 16, 17, 18, 5],[14, 23, 24, 19, 6],[13, 22, 21, 20, 7],[12, 11, 10, 9, 8]]`.

### Solution
```javascript
function spiralArray(n) {
  // Create an empty n x n matrix filled with null values
  let matrix = Array.from({ length: n }, () => Array(n).fill(null));
  
  // Define initial boundaries
  let top = 0, bottom = n - 1, left = 0, right = n - 1;
  let value = 0;

  while (top <= bottom && left <= right) {
    // Traverse from left to right on the top row
    for (let i = left; i <= right; i++) {
      matrix[top][i] = value++;
    }
    top++;

    // Traverse from top to bottom on the right column
    for (let i = top; i <= bottom; i++) {
      matrix[i][right] = value++;
    }
    right--;

    // Traverse from right to left on the bottom row
    if (top <= bottom) {
      for (let i = right; i >= left; i--) {
        matrix[bottom][i] = value++;
      }
      bottom--;
    }

    // Traverse from bottom to top on the left column
    if (left <= right) {
      for (let i = bottom; i >= top; i--) {
        matrix[i][left] = value++;
      }
      left++;
    }
  }

  return matrix;
}
```