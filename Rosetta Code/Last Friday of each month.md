# Last Friday of each month

### Description

Write a function that returns the date of the last Friday of a given month for a given year.

### Tests

1. `lastFriday` should be a function.
2. `lastFriday(2018, 1)` should return a number.
3. `lastFriday(2018, 1)` should return `26`.
4. `lastFriday(2017, 2)` should return `24`.
5. `lastFriday(2012, 3)` should return `30`.
6. `lastFriday(1900, 4)` should return `27`.
7. `lastFriday(2000, 5`) should return `26`.
8. `lastFriday(2006, 6)` should return `30`.
9. `lastFriday(2010, 7)` should return `30`.
10. `lastFriday(2005, 8)` should return `26`.

### Answer:

```javascript
function lastFriday(year, month) {
    // Create a date object for the first day of the next month
    let nextMonth = new Date(year, month, 1);
    
    // Subtract one day to get the last day of the current month
    nextMonth.setDate(nextMonth.getDate() - 1);
    
    // Get the last day of the month
    let lastDay = nextMonth.getDate();
    
    // Create a date object for the last day of the month
    let lastDate = new Date(year, month - 1, lastDay);
    
    // Find the last Friday
    while (lastDate.getDay() !== 5) { // 5 corresponds to Friday
        lastDate.setDate(lastDate.getDate() - 1);
    }
    
    // Return the date of the last Friday
    return lastDate.getDate();
}

// Example usages
console.log(lastFriday(2018, 1)); // 26
console.log(lastFriday(2017, 2)); // 24
console.log(lastFriday(2012, 3)); // 30
console.log(lastFriday(1900, 4)); // 27
console.log(lastFriday(2000, 5)); // 26
console.log(lastFriday(2006, 6)); // 30
console.log(lastFriday(2010, 7)); // 30
console.log(lastFriday(2005, 8)); // 26
```