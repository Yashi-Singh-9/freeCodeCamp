# Leap Year

### Description

Determine whether a given year is a leap year in the Gregorian calendar.

### Tests

1. `isLeapYear` should be a function.
2. `isLeapYear()` should return a boolean.
3. `isLeapYear(2018)` should return `false`.
4. `isLeapYear(2016)` should return `true`.
5. `isLeapYear(2000)` should return `true`.
6. `isLeapYear(1900)` should return `false`.
7. `isLeapYear(1996)` should return `true`.
8. `isLeapYear(1800)` should return `false`.

### Answer:

```javascript
function isLeapYear(year) {
    // Check if the year is divisible by 4
    if (year % 4 === 0) {
        // If it is divisible by 100, it should also be divisible by 400 to be a leap year
        if (year % 100 === 0) {
            return year % 400 === 0; // true if divisible by 400, else false
        }
        return true; // It is a leap year
    }
    return false; // Not a leap year
}

// Test cases
console.log(isLeapYear(2018)); // false
console.log(isLeapYear(2016)); // true
console.log(isLeapYear(2000)); // true
console.log(isLeapYear(1900)); // false
console.log(isLeapYear(1996)); // true
console.log(isLeapYear(1800)); // false
```