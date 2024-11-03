# Sorting algorithms/Bead sort

### Description

A bead sort starts by creating a matrix of zeroes whose length is equal to the value of the largest element in the input array. The matrix is transformed by adding one to all elements between the zeroth index and the index indicated by the current element. This process is repeated, until you have filled the matrix.

Iterating over the matrix, summing the number of elements greater than zero, then decreasing the value of each element by one yields the sorted array.

Note: Each element in the input array is unique.

Sort an array of positive integers using the Bead Sort Algorithm.

### Tests

1. `beadSort` should be a function.
2. `beadSort([25, 32, 12, 7, 20])` should return an array.
3. `beadSort([25, 32, 12, 7, 20])` should return `[7, 12, 20, 25, 32]`.
4. `beadSort([38, 45, 35, 8, 13])` should return `[8, 13, 35, 38, 45]`.
5. `beadSort([43, 36, 20, 34, 24])` should return `[20, 24, 34, 36, 43]`.
6. `beadSort([12, 33, 26, 18, 1, 16, 38])` should return `[1, 12, 16, 18, 26, 33, 38]`.
7. `beadSort([3, 39, 48, 16, 1, 4, 29])` should return `[1, 3, 4, 16, 29, 39, 48]`.

### Solution:

```javascript
function beadSort(arr) {
    if (!Array.isArray(arr) || arr.length === 0) return arr;

    // Find the maximum value in the array
    const max = Math.max(...arr);
    
    // Create the matrix initialized with zeros
    const beads = Array.from({ length: arr.length }, () => Array(max).fill(0));

    // Drop beads for each element in the input array
    for (let i = 0; i < arr.length; i++) {
        for (let j = 0; j < arr[i]; j++) {
            beads[i][j] = 1;
        }
    }

    // Sort beads by gravity, counting beads in each column and then adjusting each row
    for (let j = 0; j < max; j++) {
        // Count the beads in each column
        let sum = 0;
        for (let i = 0; i < arr.length; i++) {
            sum += beads[i][j];
            beads[i][j] = 0; // Clear the column
        }
        
        // Let the beads fall to the bottom of the matrix
        for (let i = arr.length - sum; i < arr.length; i++) {
            beads[i][j] = 1;
        }
    }

    // Convert bead matrix back to sorted array
    const sortedArray = [];
    for (let i = 0; i < arr.length; i++) {
        let count = 0;
        for (let j = 0; j < max; j++) {
            if (beads[i][j] === 1) count++;
        }
        sortedArray.push(count);
    }

    return sortedArray;
}

// Test cases
console.log(beadSort([25, 32, 12, 7, 20])); // [7, 12, 20, 25, 32]
console.log(beadSort([38, 45, 35, 8, 13])); // [8, 13, 35, 38, 45]
console.log(beadSort([43, 36, 20, 34, 24])); // [20, 24, 34, 36, 43]
console.log(beadSort([12, 33, 26, 18, 1, 16, 38])); // [1, 12, 16, 18, 26, 33, 38]
console.log(beadSort([3, 39, 48, 16, 1, 4, 29])); // [1, 3, 4, 16, 29, 39, 48]
```