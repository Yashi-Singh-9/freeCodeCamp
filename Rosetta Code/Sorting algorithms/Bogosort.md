# Sorting algorithms/Bogosort

### Description

Bogosort a list of numbers.

Bogosort simply shuffles a collection randomly until it is sorted.

"Bogosort" is a perversely inefficient algorithm only used as an in-joke.

Its average run-time is O(n!) because the chance that any given shuffle of a set will end up in sorted order is about one in n factorial, and the worst case is infinite since there's no guarantee that a random shuffling will ever produce a sorted sequence.

Its best case is O(n) since a single pass through the elements may suffice to order them.

Pseudocode:
```
while not InOrder(list) do
  Shuffle(list)
done
```

### Tests

1. `bogosort` should be a function.
2. `bogosort([25, 32, 12, 7, 20])` should return an array.
3. `bogosort([25, 32, 12, 7, 20])` should return `[7, 12, 20, 25, 32]`.
4. `bogosort([38, 45, 35, 8, 13])` should return `[8, 13, 35, 38, 45]`.
5. `bogosort([43, 36, 20, 34, 24])` should return `[20, 24, 34, 36, 43]`.
6. `bogosort([12, 33, 26, 18, 1, 16, 38])` should return `[1, 12, 16, 18, 26, 33, 38]`.
7. `bogosort([3, 39, 48, 16, 1, 4, 29])` should return `[1, 3, 4, 16, 29, 39, 48]`.

### Solution

```javascript
function bogosort(arr) {
    // Function to check if the array is sorted
    const isSorted = (array) => {
        for (let i = 0; i < array.length - 1; i++) {
            if (array[i] > array[i + 1]) {
                return false;
            }
        }
        return true;
    };

    // Function to shuffle the array randomly
    const shuffle = (array) => {
        for (let i = array.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [array[i], array[j]] = [array[j], array[i]]; // Swap elements
        }
    };

    // Continue shuffling until the array is sorted
    while (!isSorted(arr)) {
        shuffle(arr);
    }

    return arr;
}

// Test cases
console.log(bogosort([25, 32, 12, 7, 20])); // Should return sorted array
console.log(bogosort([38, 45, 35, 8, 13])); // Should return sorted array
console.log(bogosort([43, 36, 20, 34, 24])); // Should return sorted array
console.log(bogosort([12, 33, 26, 18, 1, 16, 38])); // Should return sorted array
console.log(bogosort([3, 39, 48, 16, 1, 4, 29])); // Should return sorted array
```