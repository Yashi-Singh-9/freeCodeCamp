# Sorting algorithms/Stooge sort

### Description

Write a function to perform Stooge Sort on an array of integers. The function should return a sorted array.

The Stooge Sort algorithm is as follows:
```
algorithm stoogesort(array L, i = 0, j = length(L)-1)
  if L[j] < L[i] then
    L[i] ↔ L[j]
  if j - i > 1 then
    t := (j - i + 1)/3
    stoogesort(L, i , j-t)
    stoogesort(L, i+t, j )
    stoogesort(L, i , j-t)
  return L
```

### Tests

1. `stoogeSort` should be a function.
2. `stoogeSort([25, 32, 12, 7, 20])` should return an array.
3. `stoogeSort([25, 32, 12, 7, 20])` should return `[7, 12, 20, 25, 32]`.
4. `stoogeSort([38, 45, 35, 8, 13])` should return `[8, 13, 35, 38, 45]`.
5. `stoogeSort([43, 36, 20, 34, 24])` should return `[20, 24, 34, 36, 43]`.
6. `stoogeSort([12, 33, 26, 18, 1, 16, 38])` should return `[1, 12, 16, 18, 26, 33, 38]`.
7. `stoogeSort([3, 39, 48, 16, 1, 4, 29])` should return `[1, 3, 4, 16, 29, 39, 48]`.

### Solution:

```javascript
function stoogeSort(arr, i = 0, j = arr.length - 1) {
    // Base case: if the last element is smaller than the first, swap them
    if (arr[j] < arr[i]) {
        [arr[i], arr[j]] = [arr[j], arr[i]];
    }

    // Recursive case: sort only if there are more than two elements
    if (j - i > 1) {
        let t = Math.floor((j - i + 1) / 3);

        // Sort the initial two-thirds
        stoogeSort(arr, i, j - t);
        
        // Sort the final two-thirds
        stoogeSort(arr, i + t, j);
        
        // Sort the initial two-thirds again
        stoogeSort(arr, i, j - t);
    }
    return arr;
}
```