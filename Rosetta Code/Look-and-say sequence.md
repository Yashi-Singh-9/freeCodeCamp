# Look-and-say sequence

### Description

The Look and say sequence is a recursively defined sequence of numbers.

Sequence Definition

- Take a decimal number
- Look at the number, visually grouping consecutive runs of the same digit.
- Say the number, from left to right, group by group; as how many of that digit there are - followed by the digit grouped.

This becomes the next number of the sequence.
An example:

- Starting with the number 1, you have one 1 which produces 11
- Starting with 11, you have two 1's. I.E.: 21
- Starting with 21, you have one 2, then one 1. I.E.: (12)(11) which becomes 1211
- Starting with 1211, you have one 1, one 2, then two 1's. I.E.: (11)(12)(21) which becomes 111221

---

Write a function that accepts a string as a parameter, processes it, and returns the resultant string.

### Tests

1. `lookAndSay` should be a function.
2. `lookAndSay("1")` should return a string.
3. `lookAndSay("1")` should return `"11"`.
4. `lookAndSay("11")` should return `"21"`.
5. `lookAndSay("21")` should return `"1211"`.
6. `lookAndSay("1211")` should return `"111221"`.
7. `lookAndSay("3542")` should return `"13151412"`.

### Solution:

```javascript
function lookAndSay(input) {
    let result = '';
    let count = 1;
    
    for (let i = 0; i < input.length; i++) {
        // Check if the current digit is the same as the next one
        if (input[i] === input[i + 1]) {
            count++;
        } else {
            // Append the count and the digit to the result
            result += count.toString() + input[i];
            count = 1; // Reset count for the next new digit
        }
    }
    
    return result;
}

// Test cases
console.log(lookAndSay("1"));      // Output: "11"
console.log(lookAndSay("11"));     // Output: "21"
console.log(lookAndSay("21"));     // Output: "1211"
console.log(lookAndSay("1211"));   // Output: "111221"
console.log(lookAndSay("3542"));   // Output: "13151412"
```