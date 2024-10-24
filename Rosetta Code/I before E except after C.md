# I before E except after C

### Description

["I before E, except after C"](https://rosettacode.org/wiki/I_before_E_except_after_C) is a general rule for English language spelling. If one is unsure whether a word is spelled with the digraph `ei` or `ie`, the rhyme suggests that the correct order is `ie` unless the preceding letter is `c`, in which case it may be `ei`.

Using the words provided, check if the two sub-clauses of the phrase are plausible individually:

1. "I before E when not preceded by C".
2. "E before I when preceded by C".

If both sub-phrases are plausible then the original phrase can be said to be plausible.

---

Write a function that accepts a word and check if the word follows this rule. The function should return true if the word follows the rule and false if it does not.

### Tests

1. `IBeforeExceptC` should be a function.
2. `IBeforeExceptC("receive")` should return a boolean.
3. `IBeforeExceptC("receive")` should return `true`.
4. `IBeforeExceptC("science")` should return `false`.
5. `IBeforeExceptC("imperceivable")` should return `true`.
6. `IBeforeExceptC("inconceivable")` should return `true`.
7. `IBeforeExceptC("insufficient")` should return `false`.
8. `IBeforeExceptC("omniscient")` should return `false`.

### Answer:

```javascript
function IBeforeExceptC(word) {
    // Check for "ei" preceded by "c"
    if (word.match(/cei/)) {
        return true; // valid: 'ei' after 'c'
    }
    
    // Check for "ie" not preceded by "c"
    if (word.match(/[^c]ie/)) {
        return true; // valid: 'ie' not after 'c'
    }
    
    // Check for invalid cases
    if (word.match(/cie/)) {
        return false; // invalid: 'ie' after 'c'
    }
    
    if (word.match(/[^c]ei/)) {
        return false; // invalid: 'ei' not after 'c'
    }
    
    // If no ie or ei found, assume it follows the rule
    return true;
}

// Test cases
console.log(IBeforeExceptC("receive"));       // true
console.log(IBeforeExceptC("science"));       // false
console.log(IBeforeExceptC("imperceivable")); // true
console.log(IBeforeExceptC("inconceivable")); // true
console.log(IBeforeExceptC("insufficient"));  // false
console.log(IBeforeExceptC("omniscient"));    // false
```