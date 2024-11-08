# Sorting algorithms/Shell sort

### Description

Write a function to sort an array of elements using the Shell sort algorithm, a diminishing increment sort. The function should return the sorted array.

The Shell sort (also known as Shellsort or Shell's method) is named after its inventor, Donald Shell, who published the algorithm in 1959.

Shell sort is a sequence of interleaved insertion sorts based on an increment sequence. The increment size is reduced after each pass until the increment size is 1.

With an increment size of 1, the sort is a basic insertion sort, but by this time the data is guaranteed to be almost sorted, which is insertion sort's "best case".

Any sequence will sort the data as long as it ends in 1, but some work better than others.

Empirical studies have shown a geometric increment sequence with a ratio of about 2.2 work well in practice.

### Tests

1. `shellSort` should be a function.
2. `shellSort([25, 32, 12, 7, 20])` should return an array.
3. `shellSort([25, 32, 12, 7, 20])` should return `[7, 12, 20, 25, 32]`.
4. `shellSort([38, 45, 35, 8, 13])` should return `[8, 13, 35, 38, 45]`.
5. `shellSort([43, 36, 20, 34, 24])` should return `[20, 24, 34, 36, 43]`.
6. `shellSort([12, 33, 26, 18, 1, 16, 38])` should return `[1, 12, 16, 18, 26, 33, 38]`.
7. `shellSort([3, 39, 48, 16, 1, 4, 29])` should return `[1, 3, 4, 16, 29, 39, 48]`.

### Solution

```javascript
function shellSort(arr) {
    let n = arr.length;
    // Start with a large gap, then reduce the gap
    for (let gap = Math.floor(n / 2); gap > 0; gap = Math.floor(gap / 2)) {
        // Perform a gapped insertion sort for this gap size.
        for (let i = gap; i < n; i++) {
            // Save arr[i] in temp and make a hole at position i
            let temp = arr[i];
            let j;
            
            // Shift earlier gap-sorted elements up until the correct location for arr[i] is found
            for (j = i; j >= gap && arr[j - gap] > temp; j -= gap) {
                arr[j] = arr[j - gap];
            }
            
            // Put temp (the original arr[i]) in its correct location
            arr[j] = temp;
        }
    }
    return arr;
}

// Testing the function with the given test cases
console.log(shellSort([25, 32, 12, 7, 20]));  // Output: [7, 12, 20, 25, 32]
console.log(shellSort([38, 45, 35, 8, 13]));   // Output: [8, 13, 35, 38, 45]
console.log(shellSort([43, 36, 20, 34, 24]));  // Output: [20, 24, 34, 36, 43]
console.log(shellSort([12, 33, 26, 18, 1, 16, 38])); // Output: [1, 12, 16, 18, 26, 33, 38]
console.log(shellSort([3, 39, 48, 16, 1, 4, 29]));   // Output: [1, 3, 4, 16, 29, 39, 48]
```