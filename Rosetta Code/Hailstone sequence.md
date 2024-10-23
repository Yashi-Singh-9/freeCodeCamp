# Hailstone sequence

### Description

The Hailstone sequence of numbers can be generated from a starting positive integer, `n` by:

- If `n` is `1` then the sequence ends
- If `n` is `even` then the next `n` of the sequence `= n/2`
- If `n` is `odd` then the next `n` of the sequence `= (3 * n) + 1`

The (unproven) Collatz conjecture is that the hailstone sequence for any starting number always terminates.

The hailstone sequence is also known as hailstone numbers (because the values are usually subject to multiple descents and ascents like hailstones in a cloud), or as the Collatz sequence.

---

1. Create a routine to generate the hailstone sequence for a number
2. Your function should return an array with the number less than `limit` which has the longest hailstone sequence and that sequence's length. (But don't show the actual sequence!)

### Tests

1. `hailstoneSequence` should be a function.
2. `hailstoneSequence(30)` should return an array.
3. `hailstoneSequence(30)` should return `[27, 112]`.
4. `hailstoneSequence(50000)` should return `[35655, 324]`.
5. `hailstoneSequence(100000)` should return `[77031, 351]`.

### Answer:

```javascript
function hailstoneSequenceLength(n) {
    let length = 1; // Start with the initial number
    while (n !== 1) {
        if (n % 2 === 0) {
            n = n / 2;
        } else {
            n = 3 * n + 1;
        }
        length++;
    }
    return length;
}

function hailstoneSequence(limit) {
    let maxLength = 0;
    let numberWithMaxSequence = 0;

    for (let i = 1; i < limit; i++) {
        let length = hailstoneSequenceLength(i);
        if (length > maxLength) {
            maxLength = length;
            numberWithMaxSequence = i;
        }
    }

    return [numberWithMaxSequence, maxLength];
}

// Test cases
console.log(hailstoneSequence(30));     // Expected: [27, 112]
console.log(hailstoneSequence(50000));  // Expected: [35655, 324]
console.log(hailstoneSequence(100000)); // Expected: [77031, 351]
```