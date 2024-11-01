# Luhn test of credit card numbers

### Description

The Luhn test is used by some credit card companies to distinguish valid credit card numbers from what could be a random selection of digits.

Those companies using credit card numbers that can be validated by the Luhn test have numbers that pass the following test:

1. Reverse the order of the digits in the number.
2. Take the first, third, ... and every other odd digit in the reversed digits and sum them to form the partial sum s1
3. Taking the second, fourth ... and every other even digit in the reversed digits:
    1.Multiply each digit by two and sum the digits if the answer is greater than nine to form partial sums for the even digits.
    2.Sum the partial sums of the even digits to form s2.
4.If s1 + s2 ends in zero then the original number is in the form of a valid credit card number as verified by the Luhn test.

For example, if the trial number is 49927398716:

```
Reverse the digits:
  61789372994
Sum the odd digits:
  6 + 7 + 9 + 7 + 9 + 4 = 42 = s1
The even digits:
    1, 8, 3, 2, 9
  Two times each even digit:
    2, 16, 6, 4, 18
  Sum the digits of each multiplication:
    2, 7, 6, 4, 9
  Sum the last:
    2 + 7 + 6 + 4 + 9 = 28 = s2

s1 + s2 = 70 which ends in zero which means that 49927398716 passes the Luhn test.
```
---

Write a function that will validate a number with the Luhn test. Return true if it's a valid number. Otherwise, return false.

### Tests

1. `luhnTest` should be a function.
2. `luhnTest("4111111111111111")` should return a boolean.
3. `luhnTest("4111111111111111")` should return `true`.
4. `luhnTest("4111111111111112")` should return `false`.
5. `luhnTest("49927398716")` should return `true`.
6. `luhnTest("49927398717")` should return `false`.
7. `luhnTest("1234567812345678")` should return `false`.
8. `luhnTest("1234567812345670")` should return `true`.

### Solution :

```javascript
function luhnTest(number) {
    // Convert the number to a string and reverse it
    const reversedDigits = number.toString().split('').reverse();
    
    let s1 = 0; // Sum of odd-positioned digits
    let s2 = 0; // Sum of even-positioned digits after transformation
    
    // Iterate over the reversed digits
    for (let i = 0; i < reversedDigits.length; i++) {
        let digit = parseInt(reversedDigits[i]);
        
        if (i % 2 === 0) {
            // Odd position in reversed order, add to s1
            s1 += digit;
        } else {
            // Even position in reversed order
            let doubled = digit * 2;
            // If the doubled value is more than 9, sum its digits
            if (doubled > 9) {
                doubled -= 9;
            }
            s2 += doubled;
        }
    }
    
    // The number is valid if (s1 + s2) ends in 0
    return (s1 + s2) % 10 === 0;
}

// Test cases
console.log(luhnTest("4111111111111111")); // true
console.log(luhnTest("4111111111111112")); // false
console.log(luhnTest("49927398716"));      // true
console.log(luhnTest("49927398717"));      // false
console.log(luhnTest("1234567812345678")); // false
console.log(luhnTest("1234567812345670")); // true
```