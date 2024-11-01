# Lucas-Lehmer test

### Description

Lucas-Lehmer Test: for $p$ an odd prime, the Mersenne number $2^p-1$ is prime if and only if $2^p-1$ divides $S(p-1)$ where $S(n+1)=(S(n))^2-2$, and $S(1)=4$.

---

Write a function that returns whether the given Mersenne number is prime or not.

### Tests

1. `lucasLehmer` should be a function.
2. `lucasLehmer(11)` should return a boolean.
3. `lucasLehmer(11)` should return `false`.
4. `lucasLehmer(15)` should return `false`.
5. `lucasLehmer(13)` should return `true`.
6. `lucasLehmer(17)` should return `true`.
7. `lucasLehmer(19)` should return `true`.
8. `lucasLehmer(21)` should return `false`.

### Solution

```javascript
function lucasLehmer(p) {
    // First, ensure p is an odd prime (since this test is only for Mersenne primes of form 2^p - 1)
    if (p < 2 || (p % 2 === 0)) return false;

    // Calculate Mersenne number for given p
    const M = (1 << p) - 1; // This is 2^p - 1

    // Lucas-Lehmer test initial setup
    let s = 4; // S(1) is always 4

    // Perform the Lucas-Lehmer iteration p-2 times
    for (let i = 0; i < p - 2; i++) {
        s = (s * s - 2) % M;
    }

    // If s is 0, the Mersenne number 2^p - 1 is prime
    return s === 0;
}
```