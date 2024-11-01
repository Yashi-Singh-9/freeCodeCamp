# Sort disjoint sublist

### Description

Given a list of values and a set of integer indices into that value list, the task is to sort the values at the given indices, but preserving the values at indices outside the set of those to be sorted.

Make your function work with the following list of values and set of indices:

`values: [7, 6, 5, 4, 3, 2, 1, 0]`

```
indices(0-based): {6, 1, 7}
```

Where the correct result would be:

`[7, 0, 5, 4, 3, 2, 1, 6].`

### Tests

1. `sortDisjoint` should be a function.
2. `sortDisjoint([7, 6, 5, 4, 3, 2, 1, 0], [6, 1, 7])` should return an array.
3. `sortDisjoint([7, 6, 5, 4, 3, 2, 1, 0], [6, 1, 7])` should return `[7, 0, 5, 4, 3, 2, 1, 6]`.
4. `sortDisjoint([7, 6, 5, 4, 3, 2, 1, 0], [1, 2, 5, 6])` should return `[7, 1, 2, 4, 3, 5, 6, 0]`.
5. `sortDisjoint([8, 7, 6, 5, 4, 3, 2, 1], [6, 1, 7])` should return `[8, 1, 6, 5, 4, 3, 2, 7]`.
6. `sortDisjoint([8, 7, 6, 5, 4, 3, 2, 1], [1, 3, 5, 6])` should return `[8, 2, 6, 3, 4, 5, 7, 1]`.
7. `sortDisjoint([6, 1, 7, 1, 3, 5, 6], [6, 1, 5, 4])` should return `[6, 1, 7, 1, 3, 5, 6].`

### Solution

```javascript
function sortDisjoint(values, indices) {
    // Convert the set of indices to an array and sort it
    const sortedIndices = Array.from(indices).sort((a, b) => a - b);
    
    // Extract the values at the specified indices
    const selectedValues = sortedIndices.map(index => values[index]);
    
    // Sort the extracted values
    const sortedValues = selectedValues.sort((a, b) => a - b);
    
    // Create a copy of the original values to modify
    const result = [...values];
    
    // Place the sorted values back into their original positions
    sortedIndices.forEach((index, i) => {
        result[index] = sortedValues[i];
    });
    
    return result;
}

// Example usages
console.log(sortDisjoint([7, 6, 5, 4, 3, 2, 1, 0], [6, 1, 7])); // [7, 0, 5, 4, 3, 2, 1, 6]
console.log(sortDisjoint([7, 6, 5, 4, 3, 2, 1, 0], [1, 2, 5, 6])); // [7, 1, 2, 4, 3, 5, 6, 0]
console.log(sortDisjoint([8, 7, 6, 5, 4, 3, 2, 1], [6, 1, 7])); // [8, 1, 6, 5, 4, 3, 2, 7]
console.log(sortDisjoint([8, 7, 6, 5, 4, 3, 2, 1], [1, 3, 5, 6])); // [8, 2, 6, 3, 4, 5, 7, 1]
console.log(sortDisjoint([6, 1, 7, 1, 3, 5, 6], [6, 1, 5, 4])); // [6, 1, 7, 1, 3, 5, 6]
```