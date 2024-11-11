# Sum digits of an integer

### Description

Write a function that takes a string as a parameter. This string represents a number that can be in any base (less than 37) and return the sum of its digits.

- 1<sub>10</sub> sums to 1
- 1234<sub>10</sub> sums to 10
- fe<sub>16</sub> sums to 29
- f0e<sub>16</sub> sums to 29

### Tests

1. `sumDigits` should be a function.
2. `sumDigits("1")` should return a number.
3. `sumDigits("1")` should return `1`.
4. `sumDigits("12345")` should return `15`.
5. `sumDigits("254")` should return `11`.
6. `sumDigits("fe")` should return `29`.
7. `sumDigits("f0e")` should return `29`.
8. `sumDigits("999ABCXYZ")` should return `162`.

### Solution:

```javascript
function sumDigits(str) {
  // Initialize the sum to 0
  let sum = 0;

  // Loop through each character in the string
  for (let i = 0; i < str.length; i++) {
    let char = str[i].toLowerCase(); // Convert the character to lowercase (since 'A' and 'a' are the same)
    
    // Check if the character is a valid digit in base 36 (i.e., 0-9, a-z)
    if (char >= '0' && char <= '9') {
      sum += parseInt(char, 10); // Convert to a number (base 10)
    } else if (char >= 'a' && char <= 'z') {
      sum += char.charCodeAt(0) - 'a'.charCodeAt(0) + 10; // Convert letter to number (a = 10, b = 11, ..., z = 35)
    }
  }

  return sum;
}

// Test cases
console.log(sumDigits("1"));        // 1
console.log(sumDigits("12345"));    // 15
console.log(sumDigits("254"));      // 11
console.log(sumDigits("fe"));       // 29
console.log(sumDigits("f0e"));      // 29
console.log(sumDigits("999ABCXYZ")); // 162
```