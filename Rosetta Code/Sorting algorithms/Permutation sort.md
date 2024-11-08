# Sorting algorithms/Permutation sort

### Descritpion

Write a function to implement a permutation sort, which proceeds by generating the possible permutations of the input array until discovering the sorted one. The function should return the sorted array.

Pseudocode:
```
while not InOrder(list) do
  nextPermutation(list)
done
```

### Tests

1. `permutationSort` should be a function.
2. `permutationSort([25, 32, 12, 7, 20])` should return an array.
3. `permutationSort([25, 32, 12, 7, 20])` should return `[7, 12, 20, 25, 32]`.
4. `permutationSort([38, 45, 35, 8, 13])` should return `[8, 13, 35, 38, 45]`.
5. `permutationSort([43, 36, 20, 34, 24])` should return `[20, 24, 34, 36, 43]`.
6. `permutationSort([12, 33, 26, 18, 1, 16, 38])` should return `[1, 12, 16, 18, 26, 33, 38]`.
7. `permutationSort([3, 39, 48, 16, 1, 4, 29])` should return `[1, 3, 4, 16, 29, 39, 48]`.

### Solution:

```javascript
function isSorted(arr) {
    for (let i = 0; i < arr.length - 1; i++) {
        if (arr[i] > arr[i + 1]) {
            return false;
        }
    }
    return true;
}

function nextPermutation(arr) {
    // Find the largest index `i` such that arr[i] < arr[i + 1]
    let i = arr.length - 2;
    while (i >= 0 && arr[i] >= arr[i + 1]) {
        i--;
    }

    // If no such index exists, the array is in descending order
    if (i < 0) {
        return arr.reverse();
    }

    // Find the largest index `j` such that arr[j] > arr[i]
    let j = arr.length - 1;
    while (arr[j] <= arr[i]) {
        j--;
    }

    // Swap arr[i] with arr[j]
    [arr[i], arr[j]] = [arr[j], arr[i]];

    // Reverse the part of the array after index `i`
    let left = i + 1;
    let right = arr.length - 1;
    while (left < right) {
        [arr[left], arr[right]] = [arr[right], arr[left]];
        left++;
        right--;
    }

    return arr;
}

function permutationSort(arr) {
    while (!isSorted(arr)) {
        nextPermutation(arr);
    }
    return arr;
}

// Test cases
console.log(permutationSort([25, 32, 12, 7, 20])); // Should return [7, 12, 20, 25, 32]
console.log(permutationSort([38, 45, 35, 8, 13])); // Should return [8, 13, 35, 38, 45]
console.log(permutationSort([43, 36, 20, 34, 24])); // Should return [20, 24, 34, 36, 43]
console.log(permutationSort([12, 33, 26, 18, 1, 16, 38])); // Should return [1, 12, 16, 18, 26, 33, 38]
console.log(permutationSort([3, 39, 48, 16, 1, 4, 29])); // Should return [1, 3, 4, 16, 29, 39, 48]
```