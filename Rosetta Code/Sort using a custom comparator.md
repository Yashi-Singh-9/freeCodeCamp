# Sort using a custom comparator

### Description

Write a function to sort an array (or list) of strings in order of descending length, and in ascending lexicographic order for strings of equal length.

### Tests

1. `lengthSorter` should be a function.
2. `lengthSorter(["Here", "are", "some", "sample", "strings", "to", "be", "sorted"])` should return an array.
3. `lengthSorter(["Here", "are", "some", "sample", "strings", "to", "be", "sorted"])` should return `["strings", "sample", "sorted", "Here", "some", "are", "be", "to"]`.
4. `lengthSorter(["I", "hope", "your", "day", "is", "going", "good", "?"])` should return `["going", "good", "hope", "your", "day", "is", "?","I"]`.
5. `lengthSorter(["Mine", "is", "going", "great"])` should return `["going", "great", "Mine", "is"]`.
6. `lengthSorter(["Have", "fun", "sorting", "!!"])` should return `["sorting", "Have", "fun", "!!"]`.
7. `lengthSorter(["Everything", "is", "good", "!!"])` should return `["Everything", "good", "!!", "is"]`.

### Solution:

```javascript
function lengthSorter(arr) {
    return arr.sort((a, b) => {
        // First compare by length in descending order
        if (b.length !== a.length) {
            return b.length - a.length;
        }
        // If lengths are equal, sort lexicographically in ascending order
        return a.localeCompare(b);
    });
}

// Testing the function
console.log(lengthSorter(["Here", "are", "some", "sample", "strings", "to", "be", "sorted"])); 
// Output: ["strings", "sample", "sorted", "Here", "some", "are", "be", "to"]

console.log(lengthSorter(["I", "hope", "your", "day", "is", "going", "good", "?"])); 
// Output: ["going", "good", "hope", "your", "day", "is", "?", "I"]

console.log(lengthSorter(["Mine", "is", "going", "great"])); 
// Output: ["going", "great", "Mine", "is"]

console.log(lengthSorter(["Have", "fun", "sorting", "!!"])); 
// Output: ["sorting", "Have", "fun", "!!"]

console.log(lengthSorter(["Everything", "is", "good", "!!"])); 
// Output: ["Everything", "good", "!!", "is"]
```