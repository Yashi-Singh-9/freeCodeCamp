# Date format

### Description

Return an array with two date strings of the current date with the following specifications:

- The first string's date order should be the year number, month number, and day number separated by dashes (`-`).
- The first string's year should be four digits in length.
- The first string's month and day should not contain - any leading zeros.
The second string's weekday and month names should not be abbreviated.
- The second string's day should not contain any leading zeros.

Example outputs:
```
['2007-11-23', 'Friday, November 23, 2007']
['2021-3-2', 'Tuesday, March 2, 2021']
```

### Tests

1. `getDateFormats` should be a function.
2. `getDateFormats` should return an object.
3. `getDateFormats` should return an array with 2 elements.
4. `getDateFormats` should return the correct date in the right format

### Answer:

```javascript
function getDateFormats() {
    // Get current date
    const currentDate = new Date();
    
    // Get parts of the date
    const year = currentDate.getFullYear();
    const month = currentDate.getMonth() + 1; // getMonth returns 0-11
    const day = currentDate.getDate();
    
    // Format first date as 'YYYY-M-D'
    const date1 = `${year}-${month}-${day}`;
    
    // Format second date as 'Weekday, Month D, YYYY'
    const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
    const date2 = currentDate.toLocaleDateString('en-US', options);
    
    // Return an array with both date formats
    return [date1, date2];
}

// Example usage
console.log(getDateFormats());
```