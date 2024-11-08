# Sorting algorithms/Strand sort

### Description

The Strand sort creates sorted subsets that are merged to create the final result.

Consider an `unsortedArray = [3, 1, 4, 2]`. Pick the first item `3` and copy it into a separate array. Search for any bigger item following this item. When you find the a larger item, in this case `4`, copy it to the separate array, [3, 4], and compare the following items to this new value, `4`.

After you have reached the end of the array, remove the items you copied, `[3, 4]`, and start again with the first item remaining in the `unsortedArray`, in this case `1`.

Following this process results in two sorted arrays, `[3, 4]` and `[1, 2]`. Merge these two arrays to create the `strandSortedArray`.

```
const unsortedArray = [3, 1, 4, 2];
const strandsortedArray = [1, 2, 3, 4];
```

Write a function to sort an array using the Strand sort. The function should return the sorted array.

### Tests

1. `strandSort` should be a function.
2. `strandSort([25, 32, 12, 7, 20])` should return an array.
3. `strandSort([25, 32, 12, 7, 20])` should return `[7, 12, 20, 25, 32]`.
4. `strandSort([38, 45, 35, 8, 13])` should return `[8, 13, 35, 38, 45]`.
5. `strandSort([43, 36, 20, 34, 24])` should return `[20, 24, 34, 36, 43]`.
6. `strandSort([12, 33, 26, 18, 1, 16, 38])` should return `[1, 12, 16, 18, 26, 33, 38]`.
7. `strandSort([3, 39, 48, 16, 1, 4, 29])` should return `[1, 3, 4, 16, 29, 39, 48]`.

### Solution

```javascript
function strandSort(arr) {
    // Helper function to merge two sorted arrays
    function mergeArrays(arr1, arr2) {
        let result = [];
        let i = 0, j = 0;

        // Merge the two arrays while keeping the result sorted
        while (i < arr1.length && j < arr2.length) {
            if (arr1[i] < arr2[j]) {
                result.push(arr1[i]);
                i++;
            } else {
                result.push(arr2[j]);
                j++;
            }
        }

        // Add any remaining elements from arr1 or arr2
        return result.concat(arr1.slice(i)).concat(arr2.slice(j));
    }

    // Main sorting function
    let sortedArray = [];

    // Loop until the input array is fully processed
    while (arr.length > 0) {
        let sublist = [];
        let i = 0;

        // Create a sorted sublist from the input array
        sublist.push(arr[i]); // Start with the first element
        arr.splice(i, 1);     // Remove it from the main array

        // Check remaining elements to build the sorted sublist
        while (i < arr.length) {
            if (arr[i] >= sublist[sublist.length - 1]) {
                sublist.push(arr[i]); // Add to sublist if it's in order
                arr.splice(i, 1);     // Remove from main array
            } else {
                i++;
            }
        }

        // Merge the sorted sublist with the sortedArray
        sortedArray = mergeArrays(sortedArray, sublist);
    }

    return sortedArray;
}

// Test cases
console.log(strandSort([3, 1, 4, 2]));               // Output: [1, 2, 3, 4]
console.log(strandSort([25, 32, 12, 7, 20]));        // Output: [7, 12, 20, 25, 32]
console.log(strandSort([38, 45, 35, 8, 13]));        // Output: [8, 13, 35, 38, 45]
console.log(strandSort([43, 36, 20, 34, 24]));       // Output: [20, 24, 34, 36, 43]
console.log(strandSort([12, 33, 26, 18, 1, 16, 38])); // Output: [1, 12, 16, 18, 26, 33, 38]
console.log(strandSort([3, 39, 48, 16, 1, 4, 29]));  // Output: [1, 3, 4, 16, 29, 39, 48]
```