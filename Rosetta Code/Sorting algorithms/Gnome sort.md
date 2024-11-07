# Sorting algorithms/Gnome sort

### Description

Gnome sort is a sorting algorithm which is similar to [Insertion sort](https://rosettacode.org/wiki/Sorting_algorithms/Insertion_sort), except that moving an element to its proper place is accomplished by a series of swaps, as in Bubble Sort.

The pseudocode for the algorithm is:

```
function gnomeSort(a[0..size-1])
  i := 1
  j := 2
  while i < size do
    if a[i-1] <= a[i] then
      /// for descending sort, use >= for comparison
      i := j
      j := j + 1
    else
      swap a[i-1] and a[i]
      i := i - 1
      if i = 0 then
        i := j
        j := j + 1
      endif
    endif
  done
```

---

Write a function to implement the above pseudo code. The function should return the sorted array.

### Tests

1. `gnomeSort` should be a function.
2. `gnomeSort([25, 32, 12, 7, 20])` should return an array.
3. `gnomeSort([25, 32, 12, 7, 20])` should return `[7, 12, 20, 25, 32]`.
4. `gnomeSort([38, 45, 35, 8, 13])` should return `[8, 13, 35, 38, 45]`.
5. `gnomeSort([43, 36, 20, 34, 24])` should return `[20, 24, 34, 36, 43]`.
6. `gnomeSort([12, 33, 26, 18, 1, 16, 38])` should return `[1, 12, 16, 18, 26, 33, 38]`.
7. `gnomeSort([3, 39, 48, 16, 1, 4, 29])` should return `[1, 3, 4, 16, 29, 39, 48]`.

### Solution:

```javascript
function gnomeSort(arr) {
  let i = 1;
  let j = 2;
  
  while (i < arr.length) {
    if (arr[i - 1] <= arr[i]) {
      i = j;
      j = j + 1;
    } else {
      // Swap arr[i-1] and arr[i]
      let temp = arr[i - 1];
      arr[i - 1] = arr[i];
      arr[i] = temp;

      i = i - 1;
      
      if (i === 0) {
        i = j;
        j = j + 1;
      }
    }
  }
  
  return arr;
}
```