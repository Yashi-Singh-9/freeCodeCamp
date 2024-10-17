# Convert seconds to compound duration

### Description

Implement a function which:

- takes a positive integer representing a duration in seconds as input (e.g., `100`), and
- returns a string which shows the same duration decomposed into weeks, days, hours, minutes, and seconds as detailed below (e.g., `1 min, 40 sec`).

Demonstrate that it passes the following three test-cases:

**Test Cases**
```
Input number	Output number
7259	        2 hr, 59 sec
86400	            1 d
6000000	        9 wk, 6 d, 10 hr, 40 min
```

**Details**

- The following five units should be used: 
```
Unit	    Suffix used in Output	    Conversion
week	        `wk`	                1 week = 7 days
day	        `d`	                1 day = 24 hours
hour	        `hr`	                1 hour = 60 minutes
minute	        `min`	                1 minute = 60 seconds
second	        `sec`	                         ---
```

- However, only include quantities with non-zero values in the output (e.g., return `1 d` and not `0 wk, 1 d, 0 hr, 0 min, 0 sec`).
- Give larger units precedence over smaller ones as much as possible (e.g., return `2 min, 10 sec` and not `1 min, 70 sec` or `130 sec`).
- Mimic the formatting shown in the test-cases (quantities sorted from largest unit to smallest and separated by comma+space; value and unit of each quantity separated by space).

### Tests

1. `convertSeconds` should be a function.
2. `convertSeconds(7259)` should return `2 hr, 59 sec`.
3. `convertSeconds(86400)` should return `1 d`.
4. `convertSeconds(6000000)` should return `9 wk, 6 d, 10 hr, 40 min`.

### Answer:

```javascript
function convertSeconds(seconds) {
    // Define conversion constants
    const secondsPerMinute = 60;
    const secondsPerHour = 60 * secondsPerMinute;
    const secondsPerDay = 24 * secondsPerHour;
    const secondsPerWeek = 7 * secondsPerDay;
    
    // Calculate each unit
    const weeks = Math.floor(seconds / secondsPerWeek);
    seconds %= secondsPerWeek;
    const days = Math.floor(seconds / secondsPerDay);
    seconds %= secondsPerDay;
    const hours = Math.floor(seconds / secondsPerHour);
    seconds %= secondsPerHour;
    const minutes = Math.floor(seconds / secondsPerMinute);
    seconds %= secondsPerMinute;
    
    // Create an array of non-zero time components with their labels
    const timeComponents = [];
    if (weeks > 0) timeComponents.push(`${weeks} wk`);
    if (days > 0) timeComponents.push(`${days} d`);
    if (hours > 0) timeComponents.push(`${hours} hr`);
    if (minutes > 0) timeComponents.push(`${minutes} min`);
    if (seconds > 0) timeComponents.push(`${seconds} sec`);
    
    // Join the components into a single string with the required format
    return timeComponents.join(', ');
}

// Test cases
console.log(convertSeconds(7259));      // Output: "2 hr, 59 sec"
console.log(convertSeconds(86400));     // Output: "1 d"
console.log(convertSeconds(6000000));   // Output: "9 wk, 6 d, 10 hr, 40 min"
```