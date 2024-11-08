# Split a character string based on change of character

### Description 

Split a (character) string into comma (plus a blank) delimited strings based on a change of character (left to right). Blanks should be treated as any other character (except they are problematic to display clearly). The same applies to commas. For instance, the string:

```
"gHHH5YY++///\\"
```

should be split as:
```
["g", "HHH", "5", "YY", "++", "///", "\\" ];
```

### Tests

1. `split` should be a function.
2. `split("hello")` should return an array.
3. `split("hello")` should return `["h", "e", "ll", "o"]`.
4. `split("commission")` should return `["c", "o", "mm", "i", "ss", "i", "o", "n"]`.
5. `split("ssss----====llloooo")` should return `["ssss", "----", "====", "lll", "oooo"]`.
6. `split("sssmmmaaammmaaat")` should return `["sss", "mmm", "aaa", "mmm", "aaa", "t"]`.
7. `split("gHHH5YY++///\\")` should return `["g", "HHH", "5", "YY", "++", "///", "\\"]`.

### Solution: 

```javascript
function split(str) {
  if (str.length === 0) return []; // Handle empty string case

  let result = [];
  let currentGroup = str[0]; // Start with the first character as the initial group

  for (let i = 1; i < str.length; i++) {
    if (str[i] === currentGroup[0]) {
      // If the current character is the same as the start of currentGroup, add to currentGroup
      currentGroup += str[i];
    } else {
      // If the character is different, push currentGroup to result and start a new group
      result.push(currentGroup);
      currentGroup = str[i];
    }
  }

  // Push the last group to the result
  result.push(currentGroup);

  return result;
}

// Test cases
console.log(split("gHHH5YY++///\\"));          // ["g", "HHH", "5", "YY", "++", "///", "\\"]
console.log(split("hello"));                   // ["h", "e", "ll", "o"]
console.log(split("commission"));              // ["c", "o", "mm", "i", "ss", "i", "o", "n"]
console.log(split("ssss----====llloooo"));     // ["ssss", "----", "====", "lll", "oooo"]
console.log(split("sssmmmaaammmaaat"));        // ["sss", "mmm", "aaa", "mmm", "aaa", "t"]
```