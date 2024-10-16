# Amicable pairs

### Description

Two integers N and M are said to be amicable pairs if N ≠ M and the sum of the proper divisors of N(sum(propDivs(N))) = M as well as sum(propDivs(M)) = N.

Example:

1184 and 1210 are an amicable pair, with proper divisors:

- 1, 2, 4, 8, 16, 32, 37, 74, 148, 296, 592 and
- 1, 2, 5, 10, 11, 22, 55, 110, 121, 242, 605 respectively.

The sum of the divisors for the first value, 1184, is 1210 and the sum of the divisors for the second value, 1210, is 1184.

---

Calculate and show here the Amicable pairs below 20,000 (there are eight).

---

### Tests

1. `amicablePairsUpTo` should be a function.
2. `amicablePairsUpTo(300)` should return `[[220,284]]`.
3. `amicablePairsUpTo(3000)` should return `[[220,284],[1184,1210],[2620,2924]]`.
4. `amicablePairsUpTo(20000)` should return `[[220,284],[1184,1210],[2620,2924],[5020,5564],[6232,6368],[10744,10856],[12285,14595],[17296,18416]]`.

### Answer:

```javascript
function properDivisors(n) {
    const divisors = [];
    for (let i = 1; i <= n / 2; i++) {
        if (n % i === 0) {
            divisors.push(i);
        }
    }
    return divisors;
}

function sumProperDivisors(n) {
    return properDivisors(n).reduce((sum, divisor) => sum + divisor, 0);
}

function amicablePairsUpTo(limit) {
    const amicablePairs = [];
    const checked = new Set(); // To avoid checking pairs twice

    for (let n = 2; n < limit; n++) {
        const m = sumProperDivisors(n);
        // Check if m is not equal to n and m is within the limit
        if (m !== n && m < limit && !checked.has(n) && !checked.has(m)) {
            if (sumProperDivisors(m) === n) {
                amicablePairs.push([n, m]);
                checked.add(n);
                checked.add(m); // Mark both numbers as checked
            }
        }
    }
    return amicablePairs;
}

// Test the function
console.log(amicablePairsUpTo(300));     // Should return [[220, 284]]
console.log(amicablePairsUpTo(3000));    // Should return [[220, 284], [1184, 1210], [2620, 2924]]
console.log(amicablePairsUpTo(20000));   // Should return [[220,284],[1184,1210],[2620,2924],[5020,5564],[6232,6368],[10744,10856],[12285,14595],[17296,18416]]
```