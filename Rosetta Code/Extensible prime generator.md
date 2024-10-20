# Extensible prime generator

### Description

Write a generator of prime numbers, in order, that will automatically adjust to accommodate the generation of any reasonably high prime.

The generator should be able to:

- Show the first `n` prime numbers
- Show the prime numbers in a range
- Show the number of primes in a range
- Show the n<sup>th</sup> prime number

The function should have two parameters. The first will receive `n` or the range as an array. The second will receive a boolean, that specifies if the function returns the prime numbers as an array or a single number(the number of primes in the range or the n<sup>th</sup> prime). According to the parameters the function should return an array.

---

### Tests

1. `primeGenerator` should be a function.
2. `primeGenerator(20, true)` should return `[2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71]`.
3. `primeGenerator([100, 150], true)` should return `[101, 103, 107, 109, 113, 127, 131, 137, 139, 149]`.
4. `primeGenerator([7700, 8000], false)` should return `30`.
5. `primeGenerator(10000, false)` should return `104729`.

### Answer:

```javascript
function primeGenerator(input, returnArray) {
    // Helper function to check if a number is prime
    function isPrime(num) {
        if (num < 2) return false;
        for (let i = 2; i * i <= num; i++) {
            if (num % i === 0) return false;
        }
        return true;
    }

    // Generator function to get the next prime number
    function* primeGen() {
        let num = 2;
        while (true) {
            if (isPrime(num)) yield num;
            num++;
        }
    }

    // Get first n prime numbers
    function getNPrimes(n) {
        const primes = [];
        const generator = primeGen();
        while (primes.length < n) {
            primes.push(generator.next().value);
        }
        return primes;
    }

    // Get prime numbers within the range [a, b]
    function getPrimesInRange(a, b) {
        const primes = [];
        const generator = primeGen();
        let prime;
        while ((prime = generator.next().value) <= b) {
            if (prime >= a) primes.push(prime);
        }
        return primes;
    }

    // Handling logic based on input
    if (typeof input === 'number') {
        if (returnArray) {
            return getNPrimes(input); // Return first n primes as an array
        } else {
            return getNPrimes(input)[input - 1]; // Return the nth prime
        }
    } else if (Array.isArray(input)) {
        const [start, end] = input;
        if (returnArray) {
            return getPrimesInRange(start, end); // Return primes in range as an array
        } else {
            return getPrimesInRange(start, end).length; // Return number of primes in range
        }
    }
}

// Tests
console.log(primeGenerator(20, true)); // [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71]
console.log(primeGenerator([100, 150], true)); // [101, 103, 107, 109, 113, 127, 131, 137, 139, 149]
console.log(primeGenerator([7700, 8000], false)); // 30
console.log(primeGenerator(10000, false)); // 104729
```