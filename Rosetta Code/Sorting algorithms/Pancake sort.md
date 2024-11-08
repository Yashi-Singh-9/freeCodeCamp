# Sorting algorithms/Pancake sort

### Description

Write a function to sort an array of integers (of any convenient size) into ascending order using Pancake sorting. The function should return the sorted array.

In short, instead of individual elements being sorted, the only operation allowed is to "flip" one end of the list, like so:
```
Before:
6 7 8 9 2 5 3 4 1

After:
9 8 7 6 2 5 3 4 1
```

Only one end of the list can be flipped; this should be the low end, but the high end is okay if it's easier to code or works better, but it must be the same end for the entire solution. (The end flipped can't be arbitrarily changed.)

### Tests

1. `pancakeSort` should be a function.
2. `pancakeSort([25, 32, 12, 7, 20])` should return an array.
3. `pancakeSort([25, 32, 12, 7, 20])` should return `[7, 12, 20, 25, 32]`.
4. `pancakeSort([38, 45, 35, 8, 13])` should return `[8, 13, 35, 38, 45]`.
5. `pancakeSort([43, 36, 20, 34, 24])` should return `[20, 24, 34, 36, 43]`.
6. `pancakeSort([12, 33, 26, 18, 1, 16, 38])` should return `[1, 12, 16, 18, 26, 33, 38]`.
7. `pancakeSort([3, 39, 48, 16, 1, 4, 29])` should return `[1, 3, 4, 16, 29, 39, 48]`.

### Solution

```javascript
function pancakeSort(arr) {
    // Function to flip the array up to index k
    function flip(arr, k) {
        let left = 0;
        while (left < k) {
            [arr[left], arr[k]] = [arr[k], arr[left]];
            left++;
            k--;
        }
    }

    // Iterate over the array to place each element in its sorted position
    for (let size = arr.length; size > 1; size--) {
        // Find the index of the maximum element in the unsorted portion of the array
        let maxIdx = 0;
        for (let i = 1; i < size; i++) {
            if (arr[i] > arr[maxIdx]) {
                maxIdx = i;
            }
        }

        // Move the maximum element to the end of the unsorted portion
        if (maxIdx !== size - 1) {
            // Flip the max element to the front if it's not already there
            if (maxIdx > 0) {
                flip(arr, maxIdx);
            }
            // Flip the max element to its correct position at the end of the unsorted portion
            flip(arr, size - 1);
        }
    }
    return arr;
}

// Test cases
console.log(pancakeSort([25, 32, 12, 7, 20]));  // Output: [7, 12, 20, 25, 32]
console.log(pancakeSort([38, 45, 35, 8, 13]));  // Output: [8, 13, 35, 38, 45]
console.log(pancakeSort([43, 36, 20, 34, 24])); // Output: [20, 24, 34, 36, 43]
console.log(pancakeSort([12, 33, 26, 18, 1, 16, 38])); // Output: [1, 12, 16, 18, 26, 33, 38]
console.log(pancakeSort([3, 39, 48, 16, 1, 4, 29]));   // Output: [1, 3, 4, 16, 29, 39, 48]
```