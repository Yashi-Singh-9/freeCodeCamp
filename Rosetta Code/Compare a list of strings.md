# Compare a list of strings

### Description

A list is an ordered set of values that may contain duplicates. Here is an example:
```
const list = [['AA',  'BB', 'CC'], ['AA', 'ACB', 'AA'], [], ['AA']];
```

Given a list of arbitrarily many strings, implement a function for each of the following conditions:

- test if they are all lexically equal
- test if every string is lexically less than the one after it (i.e. whether the list is in strict ascending order)

### Tests

1. `allEqual` should be a function.
2. `azSorted` should be a function.
3. `allEqual(["AA", "AA", "AA", "AA"])` should return true.
4. `azSorted(["AA", "AA", "AA", "AA"])` should return false.
5. `allEqual(["AA", "ACB", "BB", "CC"])` should return false.
6. `azSorted(["AA", "ACB", "BB", "CC"])` should return true.
7. `allEqual([])` should return true.
8. `azSorted([])` should return true.
9. `allEqual(["AA"])` should return true.
10. `azSorted(["AA"])` should return true.
11. `allEqual(["BB", "AA"])` should return false.
12. `azSorted(["BB", "AA"])` should return false.

### Answer:

```javascript
function allEqual(arr) {
    // If the array is empty, return true
    if (arr.length === 0) return true;

    // Get the first element
    const firstElement = arr[0];

    // Check if all elements are equal to the first one
    return arr.every(element => element === firstElement);
}

function azSorted(arr) {
    // If the array is empty or has one element, return true
    if (arr.length < 2) return true;

    // Check if every element is less than the next one
    for (let i = 0; i < arr.length - 1; i++) {
        if (arr[i] >= arr[i + 1]) {
            return false; // If not in strict ascending order
        }
    }

    return true; // If all checks passed
}

// Test cases
console.log(allEqual(["AA", "AA", "AA", "AA"])); // true
console.log(azSorted(["AA", "AA", "AA", "AA"])); // false
console.log(allEqual(["AA", "ACB", "BB", "CC"])); // false
console.log(azSorted(["AA", "ACB", "BB", "CC"])); // true
console.log(allEqual([])); // true
console.log(azSorted([])); // true
console.log(allEqual(["AA"])); // true
console.log(azSorted(["AA"])); // true
console.log(allEqual(["BB", "AA"])); // false
console.log(azSorted(["BB", "AA"])); // false
```