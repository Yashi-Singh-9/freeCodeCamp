# Longest string challenge

### Description

In this challenge, you have to find the strings that are the longest among the given strings.

---

Write a function that takes an array of strings and returns the strings that have a length equal to the longest length.

### Tests

1. `longestString` should be a function.
2. `longestString(["a", "bb", "ccc", "ee", "f", "ggg"])` should return a array.
3. `longestString(["a", "bb", "ccc", "ee", "f", "ggg"])` should return `["ccc", "ggg"]`.
4. `longestString(["afedg", "bb", "sdccc", "efdee", "f", "geegg"])` should return `["afedg", "sdccc", "efdee", "geegg"]`.
5. `longestString(["a", "bhghgb", "ccc", "efde", "fssdrr", "ggg"])` should return `["bhghgb", "fssdrr"]`.
6. `longestString(["ahgfhg", "bdsfsb", "ccc", "ee", "f", "ggdsfg"])` should return `["ahgfhg", "bdsfsb", "ggdsfg"]`.
7. `longestString(["a", "bbdsf", "ccc", "edfe", "gzzzgg"])` should return `["gzzzgg"]`.

### Solution

```javascript
function longestString(strings) {
    // Check if the input array is empty
    if (strings.length === 0) {
        return [];
    }

    // Find the maximum length of the strings
    const maxLength = Math.max(...strings.map(s => s.length));

    // Filter and return strings that have the maximum length
    return strings.filter(s => s.length === maxLength);
}

// Test cases
console.log(longestString(["a", "bb", "ccc", "ee", "f", "ggg"])); // ["ccc", "ggg"]
console.log(longestString(["afedg", "bb", "sdccc", "efdee", "f", "geegg"])); // ["afedg", "sdccc", "efdee", "geegg"]
console.log(longestString(["a", "bhghgb", "ccc", "efde", "fssdrr", "ggg"])); // ["bhghgb", "fssdrr"]
console.log(longestString(["ahgfhg", "bdsfsb", "ccc", "ee", "f", "ggdsfg"])); // ["ahgfhg", "bdsfsb", "ggdsfg"]
console.log(longestString(["a", "bbdsf", "ccc", "edfe", "gzzzgg"])); // ["gzzzgg"]
```