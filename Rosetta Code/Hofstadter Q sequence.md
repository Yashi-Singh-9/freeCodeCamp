# Hofstadter Q sequence

The Hofstadter Q sequence is defined as:

```
$Q(1)=Q(2)=1, \\ Q(n)=Q\big(n-Q(n-1)\big)+Q\big(n-Q(n-2)), \quad n>2.$
```

It is defined like the Fibonacci sequence, but whereas the next term in the Fibonacci sequence is the sum of the previous two terms, in the Q sequence the previous two terms tell you how far to go back in the Q sequence to find the two numbers to sum to make the next term of the sequence.

---

Implement the Hofstadter Q Sequence equation as a function. The function should accept number, n, and return an integer.

### Tests

1. `hofstadterQ` should be a function.
2. `hofstadterQ()` should return `integer`
3. `hofstadterQ(1000)` should return `502`
4. `hofstadterQ(1500)` should return `755`
5. `hofstadterQ(2000)` should return `1005`
6. `hofstadterQ(2500)` should return `1261`

### Answer:

```javascript
function hofstadterQ(n) {
    // Create an array to store computed values, with base cases defined
    const Q = [0, 1, 1]; // Index 0 is unused for convenience (1-based index)

    // Compute values for Q(3) to Q(n)
    for (let i = 3; i <= n; i++) {
        const Qn1 = Q[i - Q[i - 1]]; // Q(n - Q(n-1))
        const Qn2 = Q[i - Q[i - 2]]; // Q(n - Q(n-2))
        Q[i] = Qn1 + Qn2; // Q(n) = Q(n - Q(n-1)) + Q(n - Q(n-2))
    }

    return Q[n]; // Return the nth value
}

// Example usage:
console.log(hofstadterQ(1000)); // Output: 502
console.log(hofstadterQ(1500)); // Output: 755
console.log(hofstadterQ(2000)); // Output: 1005
console.log(hofstadterQ(2500)); // Output: 1261
```