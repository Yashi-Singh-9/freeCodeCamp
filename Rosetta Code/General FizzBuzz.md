# General FizzBuzz

### Description

Write a generalized version of [FizzBuzz](https://rosettacode.org/wiki/FizzBuzz) that works for any list of factors, along with their words.

This is basically a "fizzbuzz" implementation where the rules of the game are supplied to the user. Create a function to implement this. The function should take two parameters.

The first will be an array with the FizzBuzz rules. For example: `[ [3, "Fizz"] , [5, "Buzz"] ]`.

This indicates that `Fizz` should be printed if the number is a multiple of 3 and `Buzz` if it is a multiple of 5. If it is a multiple of both then the strings should be concatenated in the order specified in the array. In this case, `FizzBuzz` if the number is a multiple of 3 and 5.

The second parameter is the number for which the function should return a string as stated above.

### Tests

1. `genFizzBuzz` should be a function.
2. `genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 6)` should return a string.
3. `genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 6)` should return `"Fizz"`.
4. `genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 10)` should return `"Buzz"`.
5. `genFizzBuzz([[3, "Buzz"],[5, "Fizz"]], 12)` should return `"Buzz"`.
6. `genFizzBuzz([[3, "Buzz"],[5, "Fizz"]], 13)` should return `"13"`.
7. `genFizzBuzz([[3, "Buzz"],[5, "Fizz"]], 15)` should return `"BuzzFizz"`.
8. `genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 15)` should return `"FizzBuzz"`.
9. `genFizzBuzz([[3, "Fizz"],[5, "Buzz"],[7, "Baxx"]], 105)` should return `"FizzBuzzBaxx"`.

### Solution:

```javascript
function genFizzBuzz(rules, num) {
    let result = '';

    // Iterate over each rule in the rules array
    for (let i = 0; i < rules.length; i++) {
        const [factor, word] = rules[i];
        
        // Check if the number is divisible by the factor
        if (num % factor === 0) {
            result += word;
        }
    }

    // If result is still an empty string, return the number as a string
    return result === '' ? num.toString() : result;
}

// Test cases
console.log(genFizzBuzz([[3, "Fizz"], [5, "Buzz"]], 6));    // "Fizz"
console.log(genFizzBuzz([[3, "Fizz"], [5, "Buzz"]], 10));   // "Buzz"
console.log(genFizzBuzz([[3, "Buzz"], [5, "Fizz"]], 12));   // "Buzz"
console.log(genFizzBuzz([[3, "Buzz"], [5, "Fizz"]], 13));   // "13"
console.log(genFizzBuzz([[3, "Buzz"], [5, "Fizz"]], 15));   // "BuzzFizz"
console.log(genFizzBuzz([[3, "Fizz"], [5, "Buzz"]], 15));   // "FizzBuzz"
console.log(genFizzBuzz([[3, "Fizz"], [5, "Buzz"], [7, "Baxx"]], 105)); // "FizzBuzzBaxx"
```