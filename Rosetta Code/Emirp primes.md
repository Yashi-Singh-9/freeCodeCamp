# Emirp primes

### Description

An emirp (prime spelled backwards) are primes that when reversed (in their decimal representation) are a different prime.

---

Write a function that:

- Shows the first `n` emirp numbers.
- Shows the emirp numbers in a range.
- Shows the number of emirps in a range.
- Shows the n<sup>th</sup> emirp number.

The function should accept two parameters. The first will receive `n` or the range as an array. The second will receive a boolean, that specifies if the function returns the emirps as an array or a single number (the number of primes in the range or the n<sup>th</sup> prime). According to the parameters the function should return an array or a number.

---

### Tests

1. `emirps` should be a function.
2. `emirps(20,true)` should return `[13,17,31,37,71,73,79,97,107,113,149,157,167,179,199,311,337,347,359,389]`
3. `emirps(1000)` should return `70529`
4. `emirps([7700,8000],true)` should return `[7717,7757,7817,7841,7867,7879,7901,7927,7949,7951,7963]`
5. `emirps([7700,8000],false)` should return `11`

### Answer:

```javascript
function isPrime(num) {
    if (num <= 1) return false;
    for (let i = 2; i <= Math.sqrt(num); i++) {
        if (num % i === 0) return false;
    }
    return true;
}

function reverseNumber(num) {
    return parseInt(num.toString().split('').reverse().join(''), 10);
}

function isEmirp(num) {
    if (!isPrime(num)) return false;
    const reversedNum = reverseNumber(num);
    return reversedNum !== num && isPrime(reversedNum);
}

function emirps(param1, param2) {
    const emirpList = [];
    
    if (typeof param1 === 'number') {  // Case for n or nth emirp
        let count = 0;
        let current = 2;  // Start from the smallest prime number

        while (count < param1) {
            if (isEmirp(current)) {
                emirpList.push(current);
                count++;
            }
            current++;
        }

        return param2 ? emirpList : emirpList[emirpList.length - 1];  // Return as array or nth emirp

    } else if (Array.isArray(param1) && param1.length === 2) {  // Case for range
        const [start, end] = param1;
        let count = 0;

        for (let num = start; num <= end; num++) {
            if (isEmirp(num)) {
                emirpList.push(num);
                count++;
            }
        }

        return param2 ? emirpList : count;  // Return emirps in the range as array or count
    }
}

// Example usage
console.log(emirps(20, true));  // Should return the first 20 emirp numbers
console.log(emirps(1000, false));  // Should return the 1000th emirp number
console.log(emirps([7700, 8000], true));  // Should return emirps in that range as an array
console.log(emirps([7700, 8000], false));  // Should return the count of emirps in that range
```