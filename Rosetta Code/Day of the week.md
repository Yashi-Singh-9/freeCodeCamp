# Day of the week

### Description

A company decides that whenever Xmas falls on a Sunday they will give their workers all extra paid holidays so that, together with any public holidays, workers will not have to work the following week (between the 25th of December and the first of January).

---

Write a function that takes a start year and an end year and return an array of all the years where the 25th of December will be a Sunday.

---

### Tests

1. `findXmasSunday` should be a function.
2. `findXmasSunday(2000, 2100)` should return an array.
3. `findXmasSunday(1970, 2017)` should return `[1977, 1983, 1988, 1994, 2005, 2011, 2016]`
4. `findXmasSunday(2008, 2121)` should return `[2011, 2016, 2022, 2033, 2039, 2044, 2050, 2061, 2067, 2072, 2078, 2089, 2095, 2101, 2107, 2112, 2118]`

### Answer:
```javascript
function findXmasSunday(startYear, endYear) {
    // Initialize an empty array to hold the years
    const yearsWithXmasSunday = [];
    
    // Iterate through the range of years
    for (let year = startYear; year <= endYear; year++) {
        // Create a date object for December 25th of the current year
        const date = new Date(year, 11, 25); // Month is 0-indexed (11 for December)
        
        // Check if the day of the week is Sunday (0 = Sunday)
        if (date.getDay() === 0) {
            yearsWithXmasSunday.push(year);
        }
    }
    
    return yearsWithXmasSunday;
}

// Test cases
console.log(findXmasSunday(2000, 2100)); // Example test case
console.log(findXmasSunday(1970, 2017)); // Should return [1977, 1983, 1988, 1994, 2005, 2011, 2016]
console.log(findXmasSunday(2008, 2121)); // Should return [2011, 2016, 2022, 2033, 2039, 2044, 2050, 2061, 2067, 2072, 2078, 2089, 2095, 2101, 2107, 2112, 2118]
```