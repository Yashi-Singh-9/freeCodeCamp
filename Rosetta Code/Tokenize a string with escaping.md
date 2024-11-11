# Tokenize a string with escaping

### Description

Write a function or program that can split a string at each non-escaped occurrence of a separator character.

It should accept three input parameters:

- The string
- The separator character
- The escape character

It should output a list of strings.

Rules for splitting:

- The fields that were separated by the separators, become the elements of the output list.
- Empty fields should be preserved, even at the start and end.

Rules for escaping:

- "Escaped" means preceded by an occurrence of the escape character that is not already escaped itself.
- When the escape character precedes a character that has no special meaning, it still counts as an escape (but does not do anything special).
- Each occurrences of the escape character that was used to escape something, should not become part of the output.

Demonstrate that your function satisfies the following test-case:

Given the string

one^|uno||three^^^^|four^^^|^cuatro|

and using `|` as a separator and `^` as escape character, your function should output the following array:

  ['one|uno', '', 'three^^', 'four^|cuatro', '']

### Tests

1. `tokenize` should be a function.
2. `tokenize` should return an array.
3. `tokenize('one^|uno||three^^^^|four^^^|^cuatro|', '|', '^')` should return `['one|uno', '', 'three^^', 'four^|cuatro', '']`
4. `tokenize('a@&bcd&ef&&@@hi', '&', '@')` should return `['a&bcd', 'ef', '', '@hi']`
5. `tokenize('hello^|world|how^are^you^|', '|', '^')` should return `['hello|world', 'howareyou|']`

### Solution

```javascript
function tokenize(inputString, separator, escapeChar) {
    let result = [];
    let currentToken = '';
    let escaped = false;

    // Loop through each character of the input string
    for (let i = 0; i < inputString.length; i++) {
        let char = inputString[i];

        // Check for escape character
        if (escaped) {
            // If the previous character was escapeChar, then current char is part of the token
            currentToken += char;
            escaped = false;
        } else if (char === escapeChar) {
            // If we encounter an escape character, set the flag
            escaped = true;
        } else if (char === separator) {
            // If we encounter a separator and we're not in escape mode, push the current token
            result.push(currentToken);
            currentToken = '';
        } else {
            // Otherwise, keep adding the character to the current token
            currentToken += char;
        }
    }

    // Add the last token (even if empty) after the loop
    result.push(currentToken);

    return result;
}

// Test case 1
console.log(tokenize('one^|uno||three^^^^|four^^^|^cuatro|', '|', '^'));
// Expected output: ['one|uno', '', 'three^^', 'four^|cuatro', '']

// Test case 2
console.log(tokenize('a@&bcd&ef&&@@hi', '&', '@'));
// Expected output: ['a&bcd', 'ef', '', '@hi']

// Test case 3
console.log(tokenize('hello^|world|how^are^you^|', '|', '^'));
// Expected output: ['hello|world', 'howareyou|']
```

