# Sorting algorithms/Cocktail sort

### Description

The [cocktail sort](https://rosettacode.org/wiki/Sorting_algorithms/Cocktail_sort) is an improvement on the Bubble Sort. Given an array of numbers, the cocktail sort will traverse the array from start to finish, moving the largest number to the end. Then, it will traverse the array backwards and move the smallest number to the start. It repeats these two passes, moving the next largest/smallest number to its correct position in the array until it is sorted.

Write a function that sorts a given array using cocktail sort.

### Tests

1. `cocktailSort` should be a function.
2. `cocktailSort([25, 32, 12, 7, 20])` should return an array.
3. `cocktailSort([25, 32, 12, 7, 20])` should return `[7, 12, 20, 25, 32]`.
4. `cocktailSort([38, 45, 35, 8, 13])` should return `[8, 13, 35, 38, 45]`.
5. `cocktailSort([43, 36, 20, 34, 24])` should return `[20, 24, 34, 36, 43]`.
6. `cocktailSort([12, 33, 26, 18, 1, 16, 38])` should return `[1, 12, 16, 18, 26, 33, 38]`.
7. `cocktailSort([3, 39, 48, 16, 1, 4, 29])` should return `[1, 3, 4, 16, 29, 39, 48]`.

### Solution:

```javascript
function cocktailSort(arr) {
    let start = 0;
    let end = arr.length - 1;
    let swapped = true;

    while (swapped) {
        // Reset the swapped flag on each pass
        swapped = false;

        // Forward pass: move the largest number to the end
        for (let i = start; i < end; i++) {
            if (arr[i] > arr[i + 1]) {
                [arr[i], arr[i + 1]] = [arr[i + 1], arr[i]]; // Swap
                swapped = true;
            }
        }
        
        // If no elements were swapped, array is sorted
        if (!swapped) break;
        
        // Decrement the end boundary, as the last element is in correct place
        end--;

        // Reset the swapped flag for the backward pass
        swapped = false;

        // Backward pass: move the smallest number to the start
        for (let i = end; i > start; i--) {
            if (arr[i] < arr[i - 1]) {
                [arr[i], arr[i - 1]] = [arr[i - 1], arr[i]]; // Swap
                swapped = true;
            }
        }

        // Increment the start boundary, as the first element is in correct place
        start++;
    }

    return arr;
}
```