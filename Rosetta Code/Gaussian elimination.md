# Gaussian elimination

### Description

Write a function to solve \(Ax = b\) using Gaussian elimination then backwards substitution.

\(A\) being an \(n \times n\) matrix. Also, \(x\) and \(b\) are \(n\) by 1 vectors.

To improve accuracy, please use partial pivoting and scaling.

### Tests

1. `gaussianElimination` should be a function.
2. `gaussianElimination([[1,1],[1,-1]], [5,1])` should return an array.
3. `gaussianElimination([[1,1],[1,-1]], [5,1])` should return `[ 3, 2 ]`.
4. `gaussianElimination([[2,3],[2,1]] , [8,4])` should return `[ 1, 2 ]`.
5. `gaussianElimination([[1,3],[5,-2]], [14,19])`should return `[ 5, 3 ]`.
6. `gaussianElimination([[1,1],[5,-1]] , [10,14])` should return `[ 4, 6 ]`.
7. `gaussianElimination([[1,2,3],[4,5,6],[7,8,8]] , [6,15,23])` should return `[ 1, 1, 1 ]`.

### Answer:

```javascript
function gaussianElimination(A, b) {
    const n = A.length;

    // Create augmented matrix [A|b]
    for (let i = 0; i < n; i++) {
        A[i].push(b[i]);
    }

    // Partial pivoting and forward elimination
    for (let i = 0; i < n; i++) {
        // Find row with the largest pivot (partial pivoting)
        let maxRow = i;
        for (let k = i + 1; k < n; k++) {
            if (Math.abs(A[k][i]) > Math.abs(A[maxRow][i])) {
                maxRow = k;
            }
        }

        // Swap the rows
        [A[i], A[maxRow]] = [A[maxRow], A[i]];

        // Scale row to make the pivot equal to 1
        const pivot = A[i][i];
        for (let j = i; j <= n; j++) {
            A[i][j] /= pivot;
        }

        // Eliminate the remaining rows
        for (let k = i + 1; k < n; k++) {
            const factor = A[k][i];
            for (let j = i; j <= n; j++) {
                A[k][j] -= factor * A[i][j];
            }
        }
    }

    // Back substitution
    const x = new Array(n).fill(0);
    for (let i = n - 1; i >= 0; i--) {
        x[i] = A[i][n];
        for (let j = i + 1; j < n; j++) {
            x[i] -= A[i][j] * x[j];
        }
    }

    return x;
}

// Test cases
console.log(gaussianElimination([[1, 1], [1, -1]], [5, 1])); // [3, 2]
console.log(gaussianElimination([[2, 3], [2, 1]], [8, 4]));  // [1, 2]
console.log(gaussianElimination([[1, 3], [5, -2]], [14, 19])); // [5, 3]
console.log(gaussianElimination([[1, 1], [5, -1]], [10, 14])); // [4, 6]
console.log(gaussianElimination([[1, 2, 3], [4, 5, 6], [7, 8, 8]], [6, 15, 23])); // [1, 1, 1]
```
