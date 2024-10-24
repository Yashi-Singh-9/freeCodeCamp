# Happy numbers

### Description

A happy number is defined by the following process:

Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals `1` (where it will stay), or it loops endlessly in a cycle which does not include `1`. Those numbers for which this process ends in `1` are happy numbers, while those that do not end in `1` are unhappy numbers.

---

Implement a function that returns true if the number is happy, or false if not.

### Tests

1. `happy` should be a function.
2. `happy(1)` should return a boolean.
3. `happy(1)` should return `true`.
4. `happy(2)` should return `false`.
5. `happy(7)` should return `true`.
6. `happy(10)` should return `true`.
7. `happy(13)` should return `true`.
8. `happy(19)` should return `true`.
9. `happy(23)` should return `true`.
10. `happy(28)` should return `true`.
11. `happy(31)` should return `true`.
12. `happy(32)` should return `true`.
13. `happy(33)` should return `false`.

### Answer:
```javascript
function happy(n) {
    const seen = new Set();
    
    while (n !== 1) {
        if (seen.has(n)) {
            return false; // Cycle detected
        }
        seen.add(n);
        
        // Calculate the sum of the squares of the digits
        n = n
            .toString()
            .split('')
            .map(Number)
            .reduce((sum, digit) => sum + digit * digit, 0);
    }
    
    return true; // Reached 1, it's a happy number
}

// Testing the function with provided examples
console.log(happy(1));  // true
console.log(happy(2));  // false
console.log(happy(7));  // true
console.log(happy(10)); // true
console.log(happy(13)); // true
console.log(happy(19)); // true
console.log(happy(23)); // true
console.log(happy(28)); // true
console.log(happy(31)); // true
console.log(happy(32)); // true
console.log(happy(33)); // false
```