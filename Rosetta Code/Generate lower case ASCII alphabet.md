# Generate lower case ASCII alphabet

### Description

Write a function to generate an array of lower case ASCII characters for a given range. For example, given the range `['a', 'd']`, the function should return `['a', 'b', 'c', 'd']`.

### Tests

1. `lascii` should be a function.
2. `lascii("a","d")` should return an array.
3. `lascii('a','d')` should return `[ 'a', 'b', 'c', 'd' ]`.
4. `lascii('c','i')` should return `[ 'c', 'd', 'e', 'f', 'g', 'h', 'i' ]`.
5. `lascii('m','q')` should return `[ 'm', 'n', 'o', 'p', 'q' ]`.
6. `lascii('k','n')` should return `[ 'k', 'l', 'm', 'n' ]`.
7. `lascii('t','z')` should return `[ 't', 'u', 'v', 'w', 'x', 'y', 'z' ]`.

### Answer:

```javascript
function lascii(start, end) {
  // Convert the starting and ending characters to their ASCII values
  let startCharCode = start.charCodeAt(0);
  let endCharCode = end.charCodeAt(0);
  
  // Create an array to hold the characters in the range
  let result = [];

  // Loop from the starting character code to the ending character code
  for (let i = startCharCode; i <= endCharCode; i++) {
    result.push(String.fromCharCode(i)); // Convert ASCII code back to character
  }

  return result;
}

// Test cases
console.log(lascii('a', 'd')); // [ 'a', 'b', 'c', 'd' ]
console.log(lascii('c', 'i')); // [ 'c', 'd', 'e', 'f', 'g', 'h', 'i' ]
console.log(lascii('m', 'q')); // [ 'm', 'n', 'o', 'p', 'q' ]
console.log(lascii('k', 'n')); // [ 'k', 'l', 'm', 'n' ]
console.log(lascii('t', 'z')); // [ 't', 'u', 'v', 'w', 'x', 'y', 'z' ]
```