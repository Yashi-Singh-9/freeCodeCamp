# Stream Merge

### Description

Write a function that takes multiple sorted arrays of items, and returns one array of sorted items.

### Tests

1. `mergeLists` should be a function.
2. `mergeLists([[1, 3, 5, 9, 10], [2, 4, 6, 7, 8]])` should return an array.
3. `mergeLists([[1, 3, 5, 9, 10], [2, 4, 6, 7, 8]])` should return `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`.
4. `mergeLists([[1, 4, 7, 10], [2, 5, 8, 11], [3, 6, 9, 12]])` should return `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]`.
5. `mergeLists([[1, 3, 9, 14, 15, 17, 28], [7, 8, 14, 14, 23, 26, 28, 29, 30], [9, 23, 25, 29]])` should return `[1, 3, 7, 8, 9, 9, 14, 14, 14, 15, 17, 23, 23, 25, 26, 28, 28, 29, 29, 30]`.
6. `mergeLists([[3, 14, 15], [2, 17, 18], [], [2, 3, 5, 7]])` should return `[2, 2, 3, 3, 5, 7, 14, 15, 17, 18]`.
7. `mergeLists([[1, 19, 1999], [17, 33, 2999, 3000], [8, 500, 3999]])` should return `[1, 8, 17, 19, 33, 500, 1999, 2999, 3000, 3999]`.

### Solution:

```javascript
function mergeLists(arrays) {
    // Use a min-heap to keep track of the smallest elements across the arrays
    const heap = [];
    const result = [];

    // Insert the first element of each array into the heap
    for (let i = 0; i < arrays.length; i++) {
        if (arrays[i].length > 0) {
            heap.push({ value: arrays[i][0], index: 0, arrayIndex: i });
        }
    }

    // Heapify the initial elements to build the min-heap
    heap.sort((a, b) => a.value - b.value);

    while (heap.length > 0) {
        // Pop the smallest element from the heap
        const { value, index, arrayIndex } = heap.shift();
        result.push(value);

        // Move to the next element in the same array, if it exists
        if (index + 1 < arrays[arrayIndex].length) {
            heap.push({ value: arrays[arrayIndex][index + 1], index: index + 1, arrayIndex: arrayIndex });
            heap.sort((a, b) => a.value - b.value);
        }
    }

    return result;
}

// Test cases
console.log(mergeLists([[1, 3, 5, 9, 10], [2, 4, 6, 7, 8]])); 
// Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

console.log(mergeLists([[1, 4, 7, 10], [2, 5, 8, 11], [3, 6, 9, 12]]));
// Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]

console.log(mergeLists([[1, 3, 9, 14, 15, 17, 28], [7, 8, 14, 14, 23, 26, 28, 29, 30], [9, 23, 25, 29]]));
// Output: [1, 3, 7, 8, 9, 9, 14, 14, 14, 15, 17, 23, 23, 25, 26, 28, 28, 29, 29, 30]

console.log(mergeLists([[3, 14, 15], [2, 17, 18], [], [2, 3, 5, 7]]));
// Output: [2, 2, 3, 3, 5, 7, 14, 15, 17, 18]

console.log(mergeLists([[1, 19, 1999], [17, 33, 2999, 3000], [8, 500, 3999]]));
// Output: [1, 8, 17, 19, 33, 500, 1999, 2999, 3000, 3999]
```