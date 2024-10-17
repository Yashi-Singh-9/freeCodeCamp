# CUSIP

### Description

A CUSIP is a nine-character alphanumeric code that identifies a North American financial security for the purposes of facilitating clearing and settlement of trades. The CUSIP was adopted as an American National Standard under Accredited Standards X9.6.

---

Write a function that takes a string as a parameter and checks if the string is valid CUSIP.

---

### Tests

1. `isCusip` should be a function.
2. `isCusip("037833100")` should return a boolean.
3. `isCusip("037833100")` should return `true`.
4. `isCusip("17275R102")` should return `true`.
5. `isCusip("38259P50a")` should return `false`.
6. `isCusip("38259P508")` should return `true`.
7. `isCusip("38259P50#")` should return `false`.
8. `isCusip("68389X105")` should return `true`.
9. `isCusip("68389X106")` should return `false`.
10. `isCusip("5949181")` should return `false`.

### Answer: 

```javascript
function isCusip(cusip) {
    // CUSIP must be exactly 9 characters long
    if (cusip.length !== 9) {
        return false;
    }

    // CUSIP can only contain uppercase letters and numbers
    const validChars = /^[0-9A-Z]+$/;
    if (!validChars.test(cusip)) {
        return false;
    }

    // Calculate check digit
    let sum = 0;
    for (let i = 0; i < 8; i++) {
        let value = cusip[i];
        
        // Convert letters to numbers (A=10, B=11, ..., Z=35)
        if (isNaN(value)) {
            value = value.charCodeAt(0) - 55;
        } else {
            value = parseInt(value, 10);
        }

        // Double every second digit
        if (i % 2 === 1) {
            value *= 2;
        }

        // If doubling results in a two-digit number, sum the digits
        if (value > 9) {
            value = Math.floor(value / 10) + (value % 10);
        }

        sum += value;
    }

    // The last digit of sum should match the last digit of the CUSIP
    const checkDigit = (10 - (sum % 10)) % 10;
    return checkDigit === parseInt(cusip[8], 10);
}

// Test cases
console.log(isCusip("037833100")); // true
console.log(isCusip("17275R102")); // true
console.log(isCusip("38259P50a")); // false
console.log(isCusip("38259P508")); // true
console.log(isCusip("38259P50#")); // false
console.log(isCusip("68389X105")); // true
console.log(isCusip("68389X106")); // false
console.log(isCusip("5949181"));   // false
```