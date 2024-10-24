# IBAN

### Description

The International Bank Account Number (IBAN) is an internationally agreed means of identifying bank accounts across national borders with a reduced risk of propagating transcription errors.

The IBAN consists of up to 34 alphanumeric characters:

- first the two-letter ISO 3166-1 alpha-2 country code
- then two check digits, and
- finally a country-specific Basic Bank Account Number (BBAN).

The check digits enable a sanity check of the bank account number to confirm its integrity even before submitting a transaction.

---

Write a function that takes IBAN string as parameter. If it is valid return true. Otherwise, return false.

### Tests

1. `isValid` should be a function.
2. `isValid("GB82 WEST 1234 5698 7654 32")` should return a boolean.
3. `isValid("GB82 WEST 1234 5698 7654 32")` should return `true`.
4. `isValid("GB82 WEST 1.34 5698 7654 32")` should return `false`.
5. `isValid("GB82 WEST 1234 5698 7654 325")` should return false.
6. `isValid("GB82 TEST 1234 5698 7654 32")` should return `false`.
7. `isValid("SA03 8000 0000 6080 1016 7519")` should return `true`.

### Answer:

```javascript
function isValid(iban) {
    // 1. Remove spaces and make it uppercase
    iban = iban.replace(/\s+/g, '').toUpperCase();

    // 2. Check basic structure: must be alphanumeric and length within 15-34 characters
    if (!/^[A-Z0-9]+$/.test(iban) || iban.length < 15 || iban.length > 34) {
        return false;
    }

    // 3. Rearrange the IBAN by moving the first 4 characters to the end
    const rearranged = iban.slice(4) + iban.slice(0, 4);

    // 4. Convert the letters to numbers (A=10, B=11, ..., Z=35)
    const numericIban = rearranged.split('').map(char => {
        if (char >= 'A' && char <= 'Z') {
            return char.charCodeAt(0) - 55; // A = 10, B = 11, ..., Z = 35
        }
        return char;
    }).join('');

    // 5. Perform the modulo 97 check
    const mod97 = BigInt(numericIban) % 97n;
    return mod97 === 1n;
}

// Test cases
console.log(isValid("GB82 WEST 1234 5698 7654 32")); // true
console.log(isValid("GB82 WEST 1.34 5698 7654 32")); // false
console.log(isValid("GB82 WEST 1234 5698 7654 325")); // false
console.log(isValid("GB82 TEST 1234 5698 7654 32")); // false
console.log(isValid("SA03 8000 0000 6080 1016 7519")); // true
```