# Self-referential sequence

### Description

There are several ways to generate a self-referential sequence. One very common one (the [Look-and-say sequence](https://rosettacode.org/wiki/Look-and-say_sequence)) is to start with a positive integer, then generate the next term by concatenating enumerated groups of adjacent alike digits:

0, 10, 1110, 3110, 132110, 1113122110, 311311222110 ...
The terms generated grow in length geometrically and never converge.

Another way to generate a self-referential sequence is to summarize the previous term.

Count how many of each alike digit there is, then concatenate the sum and digit for each of the sorted enumerated digits. Note that the first five terms are the same as for the previous sequence.

0, 10, 1110, 3110, 132110, 13123110, 23124110 ...
Sort the digits largest to smallest. Do not include counts of digits that do not appear in the previous term.

Depending on the seed value, series generated this way always either converge to a stable value or to a short cyclical pattern. (For our purposes, converge means that an element matches a previously seen element.) The sequence shown, with a seed value of 0, converges to a stable value of 1433223110 after 11 iterations. The seed value that converges most quickly is 22. It goes stable after the first element. (The next element is 22, which has been seen before.)

---

Write a function that takes the seed value as parameter, generates a self referential sequence until it converges, and returns it as an array.

### Solution

```javascript
function selfReferential(seed) {
    const sequence = [];
    let current = seed.toString();
    const seen = new Set();

    while (!seen.has(current)) {
        sequence.push(current);
        seen.add(current);
        current = generateNextTerm(current);
    }

    return sequence;

    function generateNextTerm(term) {
        const counts = {};
        
        // Count occurrences of each digit
        for (const char of term) {
            counts[char] = (counts[char] || 0) + 1;
        }

        // Create the next term from the counts sorted in descending order
        const sortedDigits = Object.keys(counts).sort((a, b) => b - a);
        let nextTerm = '';
        
        for (const digit of sortedDigits) {
            nextTerm += counts[digit] + digit;
        }

        return nextTerm;
    }
}

// Testing the function with the provided cases
console.log(selfReferential(40)); // ["40", "1410", "142110", "14123110", "1413124110", "2413125110", "151413224110", "152413225110", "251413324110", "152423224110", "152413423110"]
console.log(selfReferential(132110)); // ["132110", "13123110", "23124110", "1413223110", "1423224110", "2413323110", "1433223110"]
console.log(selfReferential(132211)); // ["132211", "132231", "232221", "134211", "14131231", "14231241", "24132231", "14233221"]
console.log(selfReferential(1413223110)); // ["1413223110", "1423224110", "2413323110", "1433223110"]
console.log(selfReferential(251413126110)); // ["251413126110", "16151413225110", "16251413226110", "26151413325110", "16251423225110", "16251413424110", "16153413225110"]
```