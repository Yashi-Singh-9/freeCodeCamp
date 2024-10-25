# Iterated digits squaring

### Description

If you add the square of the digits of a Natural number (an integer bigger than zero), you always end with either 1 or 89:

```
15 -> 26 -> 40 -> 16 -> 37 -> 58 -> 89
7 -> 49 -> 97 -> 130 -> 10 -> 1
```

---

Write a function that takes a number as a parameter and returns 1 or 89 after performing the mentioned process.

### Tests

1. `iteratedSquare` should be a function.
2. `iteratedSquare(4)` should return a number.
3. `iteratedSquare(4)` should return `89`.
4. `iteratedSquare(7)` should return `1`.
5. `iteratedSquare(15)` should return `89`.
6. `iteratedSquare(20)` should return `89`.
7. `iteratedSquare(70)` should return `1`.
8. `iteratedSquare(100)` should return `1`.

### Answer:

```javascript
function iteratedSquare(n) {
    while (n !== 1 && n !== 89) {
        n = n.toString().split('').reduce((sum, digit) => sum + Math.pow(parseInt(digit), 2), 0);
    }
    return n;
}

// Testing the function
console.log(iteratedSquare(4));    // Expected output: 89
console.log(iteratedSquare(7));    // Expected output: 1
console.log(iteratedSquare(15));   // Expected output: 89
console.log(iteratedSquare(20));   // Expected output: 89
console.log(iteratedSquare(70));   // Expected output: 1
console.log(iteratedSquare(100));  // Expected output: 1
```