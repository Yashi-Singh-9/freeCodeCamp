# Identity matrix

An identity matrix is a square matrix of size `\( n \times n \)`, where the diagonal elements are all `1`s (ones), and all the other elements are all `0`s (zeroes).

```
\(\displaystyle I_{n}=\begin{bmatrix} 1 & 0 & 0 \cr 0 & 1 & 0 \cr 0 & 0 & 1 \cr \end{bmatrix}\)
```

---

Write a function that takes a number `n` as a parameter and returns the identity matrix of order `\( n \times n \)`

### Answer:

```javascript
function idMatrix(n) {
  // Create an empty array for the matrix
  let matrix = [];
  
  // Loop through each row
  for (let i = 0; i < n; i++) {
    // Create a new row filled with 0s
    let row = Array(n).fill(0);
    
    // Set the diagonal element to 1
    row[i] = 1;
    
    // Push the row to the matrix
    matrix.push(row);
  }
  
  return matrix;
}
```