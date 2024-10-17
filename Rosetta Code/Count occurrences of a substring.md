# Count occurrences of a substring

### Description

Create a function, or show a built-in function, to count the number of non-overlapping occurrences of a substring inside a string.

The function should take two arguments:

- the first argument being the string to search, and
- the second a substring to be searched for.

It should return an integer count.

The matching should yield the highest number of non-overlapping matches.

In general, this essentially means matching from left-to-right or right-to-left.

### Tests

1. `countSubstring` should be a function.
2. `countSubstring("the three truths", "th")` should return `3`.
3. `countSubstring("ababababab", "abab")` should return `2`.
4. `countSubstring("abaabba*bbaba*bbab", "a*b")` should return `2`.

### Answer:

```javascript
function countSubstring(str, subStr) {
    let count = 0;
    let pos = 0;

    // Continue searching as long as the substring is found
    while ((pos = str.indexOf(subStr, pos)) !== -1) {
        count++;
        // Move the position to the end of the found substring to avoid overlap
        pos += subStr.length;
    }

    return count;
}

// Test cases
console.log(countSubstring("the three truths", "th")); // Output: 3
console.log(countSubstring("ababababab", "abab")); // Output: 2
console.log(countSubstring("abaabba*bbaba*bbab", "a*b")); // Output: 2
```