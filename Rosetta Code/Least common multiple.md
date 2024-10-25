# Least common multiple

### Description

The least common multiple of 12 and 18 is 36, because 12 is a factor (12 × 3 = 36), and 18 is a factor (18 × 2 = 36), and there is no positive integer less than 36 that has both factors. As a special case, if either $m$ or $n$ is zero, then the least common multiple is zero. One way to calculate the least common multiple is to iterate all the multiples of $m$, until you find one that is also a multiple of $n$. If you already have $gcd$ for [greatest common divisor](https://rosettacode.org/wiki/Greatest_common_divisor), then this formula calculates $lcm$.

$$ \operatorname{lcm}(m, n) = \frac{|m \times n|}{\operatorname{gcd}(m, n)} $$

### Tests

1. `LCM` should be a function.
2. `LCM([2, 4, 8])` should return a number.
3. `LCM([2, 4, 8])` should return `8`.
4. `LCM([4, 8, 12])` should return `24`.
5. `LCM([3, 4, 5, 12, 40])` should return `120`.
6. `LCM([11, 33, 90])` should return `990`.
7. `LCM([-50, 25, -45, -18, 90, 447])` should return `67050`.

### Answer:

```javascript
// Function to compute the GCD of two numbers
function gcd(a, b) {
    // Handle negative numbers
    a = Math.abs(a);
    b = Math.abs(b);
    
    while (b !== 0) {
        let temp = b;
        b = a % b;
        a = temp;
    }
    return a; // Return the absolute value of GCD
}

// Function to compute the LCM of two numbers using the GCD
function lcm(a, b) {
    if (a === 0 || b === 0) {
        return 0; // LCM is 0 if any number is 0
    }
    return Math.abs(a * b) / gcd(a, b);
}

// Main LCM function to compute LCM of an array of integers
function LCM(arr) {
    return arr.reduce((acc, val) => lcm(acc, val), 1); // Start with 1 as initial value
}

// Testing the LCM function with provided examples
console.log(LCM([2, 4, 8]));         // Should return 8
console.log(LCM([4, 8, 12]));        // Should return 24
console.log(LCM([3, 4, 5, 12, 40])); // Should return 120
console.log(LCM([11, 33, 90]));      // Should return 990
console.log(LCM([-50, 25, -45, -18, 90, 447])); // Should return 67050
```