# Semiprime

### Description

Semiprime numbers are natural numbers that are products of exactly two (possibly equal) [prime numbers](https://rosettacode.org/wiki/Category:Prime_Numbers).

1679  =  23 x 73

---

Write a function that returns true if a number is semiprime, or false if it is not.

### Tests

1. `isSemiPrime` should be a function.
2. `isSemiPrime(100)` should return a boolean.
3. `isSemiPrime(100)` should return `false`.
4. `isSemiPrime(504)` should return `false`.
5. `isSemiPrime(4)` should return `true`.
6. `isSemiPrime(46)` should return `true`.
7. `isSemiPrime(13)` should return `false`.
8. `isSemiPrime(74)` should return `true`.
9. `isSemiPrime(1679)` should return `true`.
10. `isSemiPrime(2)` should return `false`.
11. `isSemiPrime(95)` should return `true`.
12. `isSemiPrime(124)` should return `false`.

### Solution:

```javascript
function isSemiPrime(n) {
    // Helper function to check if a number is prime
    function isPrime(num) {
        if (num < 2) return false;
        for (let i = 2; i * i <= num; i++) {
            if (num % i === 0) return false;
        }
        return true;
    }

    // Check factors of n up to sqrt(n)
    for (let i = 2; i * i <= n; i++) {
        if (n % i === 0) {  // If i is a factor
            let otherFactor = n / i;
            // Check if both factors are prime
            if (isPrime(i) && isPrime(otherFactor)) {
                return true;
            }
        }
    }

    return false;  // Return false if no semiprime condition is met
}
```