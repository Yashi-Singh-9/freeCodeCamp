# Greatest common divisor

### Description

Write a function that returns the greatest common divisor of two integers.

### Tests

1. `gcd` should be a function.
2. `gcd(24,36)` should return a number.
3. `gcd(24,36)` should return `12`.
4. `gcd(30,48)` should return `6`.
5. `gcd(10,15)` should return `5`.
6. `gcd(100,25)` should return `25`.
7. `gcd(13,250)` should return `1`.
8. `gcd(1300,250)` should return `50`.

### Answer:

```javascript
function gcd(a, b) {
    while (b !== 0) {
        let temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

// Test cases
console.log(gcd(24, 36));   // 12
console.log(gcd(30, 48));   // 6
console.log(gcd(10, 15));   // 5
console.log(gcd(100, 25));  // 25
console.log(gcd(13, 250));  // 1
console.log(gcd(1300, 250)); // 50
```