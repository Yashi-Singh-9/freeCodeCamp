# Department Numbers

### Description

There is a highly organized city that has decided to assign a number to each of their departments:

- Police department
- Sanitation department
- Fire department

Each department can have a number between 1 and 7 (inclusive).

The three department numbers are to be unique (different from each other) and must add up to the number 12.

The Chief of the Police doesn't like odd numbers and wants to have an even number for his department.

---

Write a program which outputs all valid combinations as an array.
```
[2, 3, 7] [2, 4, 6] [2, 6, 4]
[2, 7, 3] [4, 1, 7] [4, 2, 6]
[4, 3, 5] [4, 5, 3] [4, 6, 2]
[4, 7, 1] [6, 1, 5] [6, 2, 4]
[6, 4, 2] [6, 5, 1]
```

---

### Tests

1. `combinations` should be a function.
2. `combinations([1, 2, 3], 6)` should return an Array.
3. `combinations([1, 2, 3, 4, 5, 6, 7], 12)` should return an array of length 14.
4. `combinations([1, 2, 3, 4, 5, 6, 7], 12)` should return all valid combinations.

### Answer:

```javascript
function combinations(arr, target) {
    const results = [];
    const maxNumber = Math.max(...arr);

    // Loop through all possible unique combinations of 3 numbers
    for (let i = 0; i < arr.length; i++) {
        // Only consider even numbers for the police department
        if (arr[i] % 2 === 0) {
            for (let j = 0; j < arr.length; j++) {
                if (j === i) continue; // Skip the same index
                for (let k = 0; k < arr.length; k++) {
                    if (k === i || k === j) continue; // Skip the same index
                    const police = arr[i];
                    const sanitation = arr[j];
                    const fire = arr[k];

                    // Check if the sum is equal to the target
                    if (police + sanitation + fire === target) {
                        results.push([police, sanitation, fire]);
                    }
                }
            }
        }
    }

    return results;
}

// Example calls
console.log(combinations([1, 2, 3, 4, 5, 6, 7], 12)); // Should return an array of length 14
console.log(combinations([1, 2, 3], 6)); // Should return an array with valid combinations
```