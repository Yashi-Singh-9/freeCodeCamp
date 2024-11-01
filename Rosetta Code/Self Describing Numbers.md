# Self Describing Numbers

### Description

There are several so-called "self-describing" or "self-descriptive" integers.

An integer is said to be "self-describing" if it has the property that, when digit positions are labeled 0 to N-1, the digit in each position is equal to the number of times that digit appears in the number.

For example, 2020 is a four-digit self describing number:

- position 0 has value 2 and there are two 0s in the number;
- position 1 has value 0 and there are no 1s in the number;
- position 2 has value 2 and there are two 2s;
- position 3 has value 0 and there are zero 3s;

Self-describing numbers < 100,000,000 are: 1210, 2020, 21200, 3211000, 42101000.

---

Write a function that takes a positive integer as a parameter. If it is self-describing return true. Otherwise, return false.

### Tests

1. `isSelfDescribing` should be a function.
2. `isSelfDescribing()` should return a boolean.
3. `isSelfDescribing(2020)` should return `true`.
4. `isSelfDescribing(3021)` should return `false`.
5. `isSelfDescribing(3211000)` should return `true`.

### Solution

```javascript
function isSelfDescribing(number) {
    // Convert the number to a string
    const numStr = number.toString();
    const length = numStr.length;
    
    // Create an array to count the occurrences of each digit (0-9)
    const count = Array(10).fill(0);
    
    // Count each digit's occurrences
    for (let char of numStr) {
        count[parseInt(char)]++;
    }
    
    // Check if the number is self-describing
    for (let i = 0; i < length; i++) {
        const digit = parseInt(numStr[i]);
        // Compare the digit in position i with the count of digit i
        if (digit !== count[i]) {
            return false; // Not self-describing
        }
    }
    
    return true; // It's self-describing
}

// Test cases
console.log(isSelfDescribing(2020)); // true
console.log(isSelfDescribing(3021)); // false
console.log(isSelfDescribing(3211000)); // true
console.log(isSelfDescribing(1210)); // true
console.log(isSelfDescribing(21200)); // true
console.log(isSelfDescribing(42101000)); // true
```