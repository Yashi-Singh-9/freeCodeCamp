# Comma quibbling

### Description

[Comma quibbling](https://rosettacode.org/wiki/Comma_quibbling) is a task originally set by Eric Lippert in his blog.

--- 

Write a function to generate a string output which is the concatenation of input words from a list/sequence where:

An input of no words produces the output string of just the two brace characters (`"{}"`)
An input of just one word, e.g. `["ABC"]`, produces the output string of the word inside the two braces, e.g. `"{ABC}"`
An input of two words, e.g. `["ABC", "DEF"]`, produces the output string of the two words inside the two braces with the words separated by the string `" and "`, e.g. `"{ABC and DEF}"`
An input of three or more words, e.g. `["ABC", "DEF", "G", "H"]`, produces the output string of all but the last word separated by `", "` with the last word separated by `" and "` and all within braces; e.g. `"{ABC, DEF, G and H}"`

Test your function with the following series of inputs showing your output here on this page:

- [] # (No input words).
- ["ABC"]
- ["ABC", "DEF"]
- ["ABC", "DEF", "G", "H"]

Note: Assume words are non-empty strings of uppercase characters for this task.

### Tests

1. `quibble` should be a function.
2. `quibble(["ABC"])` should return a string.
3. `quibble([])` should return "{}".
4. `quibble(["ABC"])` should return `"{ABC}"`.
5. `quibble(["ABC", "DEF"])` should return `"{ABC and DEF}"`.
6. `quibble(["ABC", "DEF", "G", "H"])` should return `"{ABC, DEF, G and H}"`.

### Answer:

```javascript
function quibble(words) {
    // Case 1: No input words
    if (words.length === 0) {
        return "{}";
    }
    
    // Case 2: One word
    if (words.length === 1) {
        return `{${words[0]}}`;
    }
    
    // Case 3: Two words
    if (words.length === 2) {
        return `{${words[0]} and ${words[1]}}`;
    }
    
    // Case 4: Three or more words
    const lastWord = words.pop(); // Remove the last word
    return `{${words.join(", ")} and ${lastWord}}`;
}

// Test the function with the specified inputs
const testCases = [
    [], 
    ["ABC"], 
    ["ABC", "DEF"], 
    ["ABC", "DEF", "G", "H"]
];

// Collect outputs
const outputs = testCases.map(quibble);
console.log(outputs);
```