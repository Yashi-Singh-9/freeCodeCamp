# Averages/Mode

### Description 

Write a function `mode` to find the value that appears most in an array.

The case where the collection is empty may be ignored. Care must be taken to handle the case where the mode is non-unique.

If it is not appropriate or possible to support a general collection, use a vector (array), if possible. If it is not appropriate or possible to support an unspecified value type, use integers.

### Tests

1. `mode` should be a function.
2. `mode([1, 3, 6, 6, 6, 6, 7, 7, 12, 12, 17])` should equal `[6]`
3. `mode([1, 2, 4, 4, 1])` should equal `[1, 4]`.

### Solution:

```javascript
function mode(arr) {
    // Check if the input array is empty
    if (arr.length === 0) return [];

    const frequencyMap = {};
    
    // Calculate frequency of each number
    for (const num of arr) {
        frequencyMap[num] = (frequencyMap[num] || 0) + 1;
    }

    let maxFrequency = 0;
    const modes = [];

    // Determine the highest frequency and collect all modes
    for (const [num, freq] of Object.entries(frequencyMap)) {
        if (freq > maxFrequency) {
            maxFrequency = freq;
            modes.length = 0; // Clear the array
            modes.push(Number(num));
        } else if (freq === maxFrequency) {
            modes.push(Number(num));
        }
    }

    return modes;
}

// Example usages:
console.log(mode([1, 3, 6, 6, 6, 6, 7, 7, 12, 12, 17])); // [6]
console.log(mode([1, 2, 4, 4, 1])); // [1, 4]
console.log(mode([])); // []
```