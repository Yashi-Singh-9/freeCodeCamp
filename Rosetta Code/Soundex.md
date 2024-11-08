# Soundex

### Description

Soundex Algorithm deals with the intentions of the words. It creates a representation for similar sounding words.

It is used for searching names and addresses. This means that the person who filled in the name, can focus on how it sounds instead of correcting the spelling of names.

For example:

If you are hearing the name `Quenci` for the first time, and misspelled it, you will get Soundex code `Q520`.

When you spell the name `Quincy` correctly next time, you will still get the same code `Q520`, which means you can link multiple name pronunciations into the same person without the need for adding every spelling.

Here is the rules:

- If a vowel (A, E, I, O, U) separates two consonants that have the same soundex code, the consonant to the right of the vowel is coded. Tymczak is coded as T-522 (T, 5 for the M, 2 for the C, Z ignored (see "Side-by-Side" rule above), 2 for the K). Since the vowel "A" separates the Z and K, the K is coded.
- If "H" or "W" separate two consonants that have the same soundex code, the consonant to the right of the vowel is not coded. Example: Ashcraft is coded A-261 (A, 2 for the S, C ignored, 6 for the R, 1 for the F). It is not coded A-226.

---

Write a function that takes a string as a parameter and returns the encoded string.

### Tests

1. `soundex` should be a function.
2. `soundex("Soundex")` should return a string.
3. `soundex("Soundex")` should return `"S532"`.
4. `soundex("Example")` should return `"E251"`.
5. `soundex("Sownteks")` should return `"S532"`.
6. `soundex("Ekzampul")` should return `"E251"`.
7. `soundex("Euler")` should return `"E460"`.
8. `soundex("Gauss")` should return `"G200"`.
9. `soundex("Hilbert")` should return `"H416"`.
10. `soundex("Knuth")` should return `"K530"`.
11. `soundex("Lloyd")` should return `"L300"`.
12. `soundex("Lukasiewicz")` should return `"L222"`.

### Solution:

```javascript
function soundex(name) {
    // Soundex mappings for consonants
    const mappings = {
        B: "1", F: "1", P: "1", V: "1",
        C: "2", G: "2", J: "2", K: "2", Q: "2", S: "2", X: "2", Z: "2",
        D: "3", T: "3",
        L: "4",
        M: "5", N: "5",
        R: "6"
    };

    // Step 1: Convert the name to uppercase and remove non-alphabetic characters
    name = name.toUpperCase().replace(/[^A-Z]/g, "");

    if (!name) return "";  // Handle empty input

    // Step 2: Initialize the code with the first letter
    let code = name[0];

    // Step 3: Encode the rest of the letters, applying Soundex rules
    let prevCode = mappings[code] || ""; // Previous Soundex digit (skip first letter)
    for (let i = 1; i < name.length; i++) {
        const char = name[i];
        const currCode = mappings[char] || ""; // Get Soundex digit for current character

        // Rule: Skip identical codes separated by vowels (A, E, I, O, U)
        // Rule: Skip identical codes separated by H or W
        if (currCode && currCode !== prevCode) {
            code += currCode;
        }
        prevCode = currCode;
    }

    // Step 4: Ensure the code has exactly 4 characters by padding or truncating
    return (code + "000").slice(0, 4);
}

// Tests
console.log(soundex("Soundex"));       // Expected: "S532"
console.log(soundex("Example"));       // Expected: "E251"
console.log(soundex("Sownteks"));      // Expected: "S532"
console.log(soundex("Ekzampul"));      // Expected: "E251"
console.log(soundex("Euler"));         // Expected: "E460"
console.log(soundex("Gauss"));         // Expected: "G200"
console.log(soundex("Hilbert"));       // Expected: "H416"
console.log(soundex("Knuth"));         // Expected: "K530"
console.log(soundex("Lloyd"));         // Expected: "L300"
console.log(soundex("Lukasiewicz"));   // Expected: "L222"
```