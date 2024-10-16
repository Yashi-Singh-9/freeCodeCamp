# Combinations

### Description

Given non-negative integers `m` and `n`, generate all size `m` combinations of the integers from `0` (zero) to `n-1` in sorted order (each combination is sorted and the entire table is sorted).

Example:

`3` comb `5` is:
```
0 1 2
0 1 3
0 1 4
0 2 3
0 2 4
0 3 4
1 2 3
1 2 4
1 3 4
2 3 4
```

### Tests

1. `combinations` should be a function.
2. `combinations(3, 5)` should return `[[0, 1, 2], [0, 1, 3], [0, 1, 4], [0, 2, 3], [0, 2, 4], [0, 3, 4], [1, 2, 3], [1, 2, 4], [1, 3, 4], [2, 3, 4]]`.
3. `combinations(4, 6)` should return `[[0,1,2,3], [0,1,2,4], [0,1,2,5], [0,1,3,4], [0,1,3,5], [0,1,4,5], [0,2,3,4], [0,2,3,5], [0,2,4,5], [0,3,4,5], [1,2,3,4], [1,2,3,5], [1,2,4,5], [1,3,4,5], [2,3,4,5]]`

### Answer:

```javascript
function combinations(m, n) {
    const result = [];

    function backtrack(start, path) {
        // If the current path has reached the desired length
        if (path.length === m) {
            result.push([...path]); // Add a copy of the path to the result
            return;
        }

        for (let i = start; i < n; i++) {
            path.push(i); // Add the current number to the path
            backtrack(i + 1, path); // Recurse with the next starting number
            path.pop(); // Backtrack by removing the last number added
        }
    }

    backtrack(0, []); // Start backtracking
    return result; // Return the result
}

// Example usage
const result1 = combinations(3, 5);
console.log(result1);
// Output: [[0, 1, 2], [0, 1, 3], [0, 1, 4], [0, 2, 3], [0, 2, 4], [0, 3, 4], [1, 2, 3], [1, 2, 4], [1, 3, 4], [2, 3, 4]]

const result2 = combinations(4, 6);
console.log(result2);
// Output: [[0, 1, 2, 3], [0, 1, 2, 4], [0, 1, 2, 5], [0, 1, 3, 4], [0, 1, 3, 5], [0, 1, 4, 5], [0, 2, 3, 4], 
//          [0, 2, 3, 5], [0, 2, 4, 5], [0, 3, 4, 5], [1, 2, 3, 4], [1, 2, 3, 5], [1, 2, 4, 5], [1, 3, 4, 5], [2, 3, 4, 5]]
```