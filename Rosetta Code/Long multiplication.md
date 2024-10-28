# Long multiplication

### Description

Explicitly implement long multiplication.

This is one possible approach to arbitrary-precision integer algebra.

---

Write a function that takes two strings of large numbers as parameters. Your function should return the product of these two large numbers as a string.

Note: In JavaScript, arithmetic operations are inaccurate with large numbers, so you will have to implement precise multiplication yourself.

### Tests

1. `mult` should be a function.
2. `mult("18446744073709551616", "18446744073709551616")` should return a string.
3. `mult("18446744073709551616", "18446744073709551616")` should return `"340282366920938463463374607431768211456"`.
4. `mult("31844674073709551616", "1844674407309551616")` should return `"58743055272886011737990786529368211456"`.
5. `mult("1846744073709551616", "44844644073709551616")` should return `"82816580680737279241781007431768211456"`.
6. `mult("1844674407370951616", "1844674407709551616")` should return `"3402823669833978308014392742590611456"`.
7. `mult("2844674407370951616", "1844674407370955616")` should return `"5247498076580334548376218009219475456"`.

### Solution

```javascript
function mult(num1, num2) {
    // Handle special case for zero
    if (num1 === "0" || num2 === "0") {
        return "0";
    }

    // Prepare to store results
    const result = Array(num1.length + num2.length).fill(0);

    // Reverse both strings to multiply from least significant digit
    const n1 = num1.split('').reverse();
    const n2 = num2.split('').reverse();

    // Multiply each digit of num1 by each digit of num2
    for (let i = 0; i < n1.length; i++) {
        for (let j = 0; j < n2.length; j++) {
            // Multiply the current digits
            const product = (n1[i] - '0') * (n2[j] - '0');
            // Add to the correct position in result
            const sum = product + result[i + j];
            result[i + j] = sum % 10; // Current digit
            result[i + j + 1] += Math.floor(sum / 10); // Carry
        }
    }

    // Remove leading zeros and convert result array back to string
    while (result[result.length - 1] === 0) {
        result.pop();
    }

    // Join the result array and reverse it to get the final answer
    return result.reverse().join('');
}

// Test cases
console.log(mult("18446744073709551616", "18446744073709551616")); // "340282366920938463463374607431768211456"
console.log(mult("31844674073709551616", "1844674407309551616")); // "58743055272886011737990786529368211456"
console.log(mult("1846744073709551616", "44844644073709551616")); // "82816580680737279241781007431768211456"
console.log(mult("1844674407370951616", "1844674407709551616")); // "3402823669833978308014392742590611456"
console.log(mult("2844674407370951616", "1844674407370955616")); // "5247498076580334548376218009219475456"
```