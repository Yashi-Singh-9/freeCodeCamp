# Balanced brackets

### Description

Determine whether a generated string of brackets is balanced; that is, whether it consists entirely of pairs of opening/closing brackets (in that order), none of which mis-nest.

Examples:
```
Input	       Output
[]	        true
][	        false
[][]	        true
][]	        false
[]][[]	        false
[[[[]]]]	true
```

### Tests

1. `isBalanced` should be a function.
2. `isBalanced("[]")` should return true.
3. `isBalanced("]][[[][][][]][")` should return false.
4. `isBalanced("[][[[[][][[[]]]]]]")` should return true.
5. `isBalanced("][")` should return false.
6. `isBalanced("[[[]]]][[]")` should return false.
7. `isBalanced("][[]")` should return false.
8. `isBalanced("][[][]][[[]]")` should return false.
9. `isBalanced("[[][]]][")` should return false.
10. `isBalanced("[[[]]][[]]]][][[")` should return false.
11. `isBalanced("[]][[]]][[[[][]]")` should return false.
12. `isBalanced("][]][[][")` should return false.
13. `isBalanced("[[]][[][]]")` should return true.
14. `isBalanced("[[]]")` should return true.
15. `isBalanced("]][]][[]][[[")` should return false.
16. `isBalanced("][]][][[")` should return false.
17. `isBalanced("][][")` should return false.
18. `isBalanced("[]]]")` should return false.
19. `isBalanced("")` should return true.

### Answer:

```javascript
function isBalanced(brackets) {
    const stack = [];
    
    for (let char of brackets) {
        if (char === '[') {
            stack.push(char);
        } else if (char === ']') {
            if (stack.length === 0) {
                return false;
            }
            stack.pop();
        }
    }
    
    return stack.length === 0;
}

// Testing the function with the given cases
console.log(isBalanced("[]"));                // true
console.log(isBalanced("]][[[][][][]]["));    // false
console.log(isBalanced("[][[[[][][[[]]]]]]")); // true
console.log(isBalanced("]["));                // false
console.log(isBalanced("[[[]]]][[]"));        // false
console.log(isBalanced("][[]"));              // false
console.log(isBalanced("][[][]][[[]]"));      // false
console.log(isBalanced("[[][]]][["));         // false
console.log(isBalanced("[[[]]][[]]]][][["));  // false
console.log(isBalanced("[]][[]]][[[[][]]"));  // false
console.log(isBalanced("][]][[][["));         // false
console.log(isBalanced("[[]][[][]]"));        // true
console.log(isBalanced("[[]]"));              // true
console.log(isBalanced("]][]][[]][[["));      // false
console.log(isBalanced("][]][][["));          // false
console.log(isBalanced("][]["));              // false
console.log(isBalanced("[]]]"));              // false
console.log(isBalanced(""));                  // true
```