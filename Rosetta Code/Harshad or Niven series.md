# Harshad or Niven series

### Description

The Harshad or Niven numbers are positive integers ≥ 1 that are divisible by the sum of their digits.

For example, `42` is a Harshad number as `42` is divisible by `(4 + 2)` without remainder.

Assume that the series is defined as the numbers in increasing order.

---

Implement a function to generate successive members of the Harshad sequence.

Use it to return an array with ten members of the sequence, starting with first Harshad number greater than `n`.

### Tests

1. `isHarshadOrNiven` should be a function.
2. `isHarshadOrNiven(10)` should return `[12, 18, 20, 21, 24, 27, 30, 36, 40, 42]`
3. `isHarshadOrNiven(400)` should return `[402, 405, 407, 408, 410, 414, 420, 423, 432, 440]`
4. `isHarshadOrNiven(1000)` should return `[1002, 1008, 1010, 1011, 1012, 1014, 1015, 1016, 1017, 1020]`

### Answer:

```javascript
function isHarshad(num) {
    // Calculate the sum of digits
    const sumOfDigits = num.toString().split('').reduce((acc, digit) => acc + Number(digit), 0);
    // Check if the number is divisible by the sum of its digits
    return num % sumOfDigits === 0;
}

function isHarshadOrNiven(n) {
    const result = [];
    let current = n + 1; // Start checking from the next integer

    while (result.length < 10) {
        if (isHarshad(current)) {
            result.push(current);
        }
        current++;
    }

    return result;
}

// Test cases
console.log(isHarshadOrNiven(10));   // [12, 18, 20, 21, 24, 27, 30, 36, 40, 42]
console.log(isHarshadOrNiven(400));  // [402, 405, 407, 408, 410, 414, 420, 423, 432, 440]
console.log(isHarshadOrNiven(1000)); // [1002, 1008, 1010, 1011, 1012, 1014, 1015, 1016, 1017, 1020]
```