# Fractran

### Description

FRACTRAN is a Turing-complete esoteric programming language invented by the mathematician John Horton Conway.

A FRACTRAN program is an ordered list of positive fractions $P = (f_1, f_2, \ldots, f_m)$, together with an initial positive integer input $n$.

The program is run by updating the integer $n$ as follows:

- for the first fraction, $f_i$, in the list for which $nf_i$ is an integer, replace $n$ with $nf_i$ ;
- repeat this rule until no fraction in the list produces an integer when multiplied by $n$, then halt.

Conway gave a program for primes in FRACTRAN:

$\dfrac{17}{91}$, $\dfrac{78}{85}$, $\dfrac{19}{51}$, $\dfrac{23}{38}$, $\dfrac{29}{33}$, $\dfrac{77}{29}$, $\dfrac{95}{23}$, $\dfrac{77}{19}$, $\dfrac{1}{17}$, $\dfrac{11}{13}$, $\dfrac{13}{11}$, $\dfrac{15}{14}$, $\dfrac{15}{2}$, $\dfrac{55}{1}$

Starting with $n=2$, this FRACTRAN program will change $n$ to $15=2\times (\frac{15}{2})$, then $825=15\times (\frac{55}{1})$, generating the following sequence of integers:

$2$, $15$, $825$, $725$, $1925$, $2275$, $425$, $390$, $330$, $290$, $770$, $\ldots$

After 2, this sequence contains the following powers of 2:

$2^2=4$, $2^3=8$, $2^5=32$, $2^7=128$, $2^{11}=2048$, $2^{13}=8192$, $2^{17}=131072$, $2^{19}=524288$, $\ldots$

which are the prime powers of 2.

---

Write a function that takes a fractran program as a string parameter and returns the first 10 numbers of the program as an array. If the result does not have 10 numbers then return the numbers as is.

### Tests

1. `fractran` should be a function.
2. `fractran("3/2, 1/3")` should return an array.
3. `fractran("3/2, 1/3")` should return `[ 2, 3, 1 ]`.
4. `fractran("3/2, 5/3, 1/5")` should return `[ 2, 3, 5, 1 ]`.
5. `fractran("3/2, 6/3")` should return `[ 2, 3, 6, 9, 18, 27, 54, 81, 162, 243 ]`.
6. `fractran("2/7, 7/2")` should return `[ 2, 7, 2, 7, 2, 7, 2, 7, 2, 7 ]`.
7. `fractran("17/91, 78/85, 19/51, 23/38, 29/33, 77/29, 95/23, 77/19, 1/17, 11/13, 13/11, 15/14, 15/2, 55/1")` should return `[ 2, 15, 825, 725, 1925, 2275, 425, 390, 330, 290 ]`.

### Answer:

```javascript
function fractran(program) {
    // Parse the program into an array of fractions
    const fractions = program.split(', ').map(f => f.split('/').map(Number));
    
    let n = 2; // Initial value of n
    let result = [n]; // Store the sequence of numbers
    
    // Run the FRACTRAN program
    while (result.length < 10) {
        let updated = false;

        for (let [numerator, denominator] of fractions) {
            if (n * numerator % denominator === 0) {
                n = (n * numerator) / denominator;
                result.push(n);
                updated = true;
                break; // Process the first fraction that divides n
            }
        }

        if (!updated) {
            break; // Stop when no fraction produces an integer
        }
    }
    
    return result;
}

// Test cases
console.log(fractran("3/2, 1/3")); // Expected output: [2, 3, 1]
console.log(fractran("3/2, 5/3, 1/5")); // Expected output: [2, 3, 5, 1]
console.log(fractran("3/2, 6/3")); // Expected output: [2, 3, 6, 9, 18, 27, 54, 81, 162, 243]
console.log(fractran("2/7, 7/2")); // Expected output: [2, 7, 2, 7, 2, 7, 2, 7, 2, 7]
console.log(fractran("17/91, 78/85, 19/51, 23/38, 29/33, 77/29, 95/23, 77/19, 1/17, 11/13, 13/11, 15/14, 15/2, 55/1")); 
// Expected output: [2, 15, 825, 725, 1925, 2275, 425, 390, 330, 290]
```