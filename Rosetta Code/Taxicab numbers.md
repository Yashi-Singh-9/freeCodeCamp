# Taxicab numbers

### Description

A taxicab number (the definition that is being used here) is a positive integer that can be expressed as the sum of two positive cubes in more than one way.

The first taxicab number is `1729`, which is:

1<sup>3</sup> + 12<sup>3</sup> and

9<sup>3</sup> + 10<sup>3</sup>.

Taxicab numbers are also known as:

- taxi numbers
- taxi-cab numbers
- taxi cab numbers
- Hardy-Ramanujan numbers

---

Write a function that returns the lowest `n` taxicab numbers. For each of the taxicab numbers, show the number as well as its constituent cubes.

### Tests

1. `taxicabNumbers` should be a function.
2. `taxicabNumbers` should return an array.
3. `taxicabNumbers` should return an array of numbers.
4. `taxicabNumbers(4)` should return [1729, 4104, 13832, 20683].
5. `taxicabNumbers(25)` should return [1729, 4104, 13832, 20683, 32832, 39312, 40033, 46683, 64232, 65728, 110656, 110808, 134379, 149389, 165464, 171288, 195841, 216027, 216125, 262656, 314496, 320264, 327763, 373464, 402597]
6. `taxicabNumbers(39)` resulting numbers from 20 - 29 should be [314496,320264,327763,373464,402597,439101,443889,513000,513856].

### Solution:

```javascript
function taxicabNumbers(n) {
    const taxicabNumbers = [];
    const sums = new Map();
    
    // Start checking cube sums for pairs of numbers a and b
    for (let a = 1; a <= 500; a++) {
        for (let b = a + 1; b <= 500; b++) { // We start from a + 1 to avoid repetition
            const sum = Math.pow(a, 3) + Math.pow(b, 3);
            
            // If the sum already exists, add the pair (a, b) to the list for that sum
            if (sums.has(sum)) {
                sums.get(sum).push([a, b]);
            } else {
                sums.set(sum, [[a, b]]);
            }
        }
    }
    
    // Now, gather the sums that have more than one pair
    for (let [sum, pairs] of sums) {
        if (pairs.length > 1) {
            taxicabNumbers.push(sum);
        }
    }
    
    // Sort the taxicab numbers in ascending order and return the first n
    taxicabNumbers.sort((a, b) => a - b);
    
    return taxicabNumbers.slice(0, n);
}

// Example usage:
console.log(taxicabNumbers(4)); // Output: [1729, 4104, 13832, 20683]
```