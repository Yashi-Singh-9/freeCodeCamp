# 24 game

### Problem Statement

The 24 Game tests a person's mental arithmetic.

The aim of the game is to arrange four numbers in a way that when evaluated, the result is 24

---

Implement a function that takes a string of four digits as its argument, with each digit from 1 to 9 (inclusive) with repetitions allowed, and returns an arithmetic expression that evaluates to the number 24. If no such solution exists, return "no solution exists".

Rules:

- Only the following operators/functions are allowed: multiplication, division, addition, subtraction.
- Division should use floating point or rational arithmetic, etc, to preserve remainders.
- Forming multiple digit numbers from the supplied digits is disallowed. (So an answer of 12+12 when given 1, 2, 2, and 1 is wrong).
- The order of the digits when given does not have to be preserved.
```
Example input	     Example output
solve24("4878");	    (7-8/8)*4
solve24("1234");	     3*1*4*2
solve24("6789");	   (6*8)/(9-7)
solve24("1127");	   (1+7)*(2+1)
```

### Tests

1. `solve24` should be a function.
2. `solve24("4878")` should return `(7-8/8)*4`, `4*(7-8/8)`, or a similar valid string
3. `solve24("1234")` should return `1*2*3*4` or a similar valid string
4. `solve24("6789")` should return `(6*8)/(9-7)`, `(8*6)/(9-7)`, or a similar valid string
5. `solve24("1127")` should return `(1+7)*(1+2)` or a similar valid string

### Answer:

```javascript
function solve24(digits) {
    const operators = ['+', '-', '*', '/'];
    
    // Helper function to evaluate expression with try-catch for division by zero
    function evaluate(a, op1, b, op2, c, op3, d) {
        const expressions = [
            `(${a}${op1}${b})${op2}(${c}${op3}${d})`,
            `((${a}${op1}${b})${op2}${c})${op3}${d}`,
            `(${a}${op1}(${b}${op2}${c}))${op3}${d}`,
            `${a}${op1}((${b}${op2}${c})${op3}${d})`,
            `${a}${op1}(${b}${op2}(${c}${op3}${d}))`
        ];
        
        for (const expr of expressions) {
            try {
                if (Math.abs(eval(expr) - 24) < 1e-6) {
                    return expr;
                }
            } catch (error) {
                // Ignore division by zero
            }
        }
        return null;
    }

    // Helper function to get all permutations of an array
    function getPermutations(array) {
        if (array.length === 1) return [array];
        const perms = [];
        for (let i = 0; i < array.length; i++) {
            const rest = getPermutations(array.slice(0, i).concat(array.slice(i + 1)));
            for (const perm of rest) {
                perms.push([array[i], ...perm]);
            }
        }
        return perms;
    }

    // Helper function to get all combinations of three operators
    function getOperatorCombinations() {
        const result = [];
        for (const op1 of operators) {
            for (const op2 of operators) {
                for (const op3 of operators) {
                    result.push([op1, op2, op3]);
                }
            }
        }
        return result;
    }

    const nums = digits.split('');
    const numPermutations = getPermutations(nums);
    const opCombinations = getOperatorCombinations();

    // Test all permutations of digits with all operator combinations
    for (const perm of numPermutations) {
        const [a, b, c, d] = perm;
        for (const ops of opCombinations) {
            const [op1, op2, op3] = ops;
            const solution = evaluate(a, op1, b, op2, c, op3, d);
            if (solution) {
                return solution;
            }
        }
    }

    return "no solution exists";
}

// Examples
console.log(solve24("4878")); // Possible output: "(7-8/8)*4"
console.log(solve24("1234")); // Possible output: "3*1*4*2"
console.log(solve24("6789")); // Possible output: "(6*8)/(9-7)"
console.log(solve24("1127")); // Possible output: "(1+7)*(2+1)"
```