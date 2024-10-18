# Element-wise operations

### Description

Implement basic element-wise matrix-matrix and scalar-matrix operations.

Implement:

- addition
- subtraction
- multiplication
- division
- exponentiation

The first parameter will be the operation to be performed, for example, "m_add" for matrix addition and "s_add" for scalar addition. The second and third parameters will be the matrices on which the operations are to be performed.

### Tests

1. `operation` should be a function.
2. `operation("m_add",[[1,2],[3,4]],[[1,2],[3,4]])` should return `[[2,4],[6,8]]`.
3. `operation("s_add",[[1,2],[3,4]],2)` should return `[[3,4],[5,6]]`.
4. `operation("m_sub",[[1,2],[3,4]],[[1,2],[3,4]])` should return `[[0,0],[0,0]]`.
5. `operation("m_mult",[[1,2],[3,4]],[[1,2],[3,4]])` should return `[[1,4],[9,16]]`.
6. `operation("m_div",[[1,2],[3,4]],[[1,2],[3,4]])` should return `[[1,1],[1,1]]`.
7. `operation("m_exp",[[1,2],[3,4]],[[1,2],[3,4]])` should return `[[1,4],[27,256]]`.
8. `operation("m_add",[[1,2,3,4],[5,6,7,8]],[[9,10,11,12],[13,14,15,16]])` should return `[[10,12,14,16],[18,20,22,24]]`.

### Solution:

```javascript
function operation(op, matrix1, matrix2) {
    if (Array.isArray(matrix2)) {
        // Matrix-matrix operations
        if (op === "m_add") {
            return matrix1.map((row, i) => row.map((val, j) => val + matrix2[i][j]));
        } else if (op === "m_sub") {
            return matrix1.map((row, i) => row.map((val, j) => val - matrix2[i][j]));
        } else if (op === "m_mult") {
            return matrix1.map((row, i) => row.map((val, j) => val * matrix2[i][j]));
        } else if (op === "m_div") {
            return matrix1.map((row, i) => row.map((val, j) => val / matrix2[i][j]));
        } else if (op === "m_exp") {
            return matrix1.map((row, i) => row.map((val, j) => Math.pow(val, matrix2[i][j])));
        }
    } else {
        // Scalar-matrix operations
        if (op === "s_add") {
            return matrix1.map(row => row.map(val => val + matrix2));
        } else if (op === "s_sub") {
            return matrix1.map(row => row.map(val => val - matrix2));
        } else if (op === "s_mult") {
            return matrix1.map(row => row.map(val => val * matrix2));
        } else if (op === "s_div") {
            return matrix1.map(row => row.map(val => val / matrix2));
        }
    }
}

// Example calls
console.log(operation("m_add", [[1, 2], [3, 4]], [[1, 2], [3, 4]])); // [[2, 4], [6, 8]]
console.log(operation("s_add", [[1, 2], [3, 4]], 2)); // [[3, 4], [5, 6]]
console.log(operation("m_sub", [[1, 2], [3, 4]], [[1, 2], [3, 4]])); // [[0, 0], [0, 0]]
console.log(operation("m_mult", [[1, 2], [3, 4]], [[1, 2], [3, 4]])); // [[1, 4], [9, 16]]
console.log(operation("m_div", [[1, 2], [3, 4]], [[1, 2], [3, 4]])); // [[1, 1], [1, 1]]
console.log(operation("m_exp", [[1, 2], [3, 4]], [[1, 2], [3, 4]])); // [[1, 4], [27, 256]]
console.log(operation("m_add", [[1, 2, 3, 4], [5, 6, 7, 8]], [[9, 10, 11, 12], [13, 14, 15, 16]])); // [[10, 12, 14, 16], [18, 20, 22, 24]]
```