# Strip control codes and extended characters from a string

### Description

The task is to strip control codes and extended characters from a string. The solution should demonstrate how to achieve each of the following results: A string with control codes and extended characters stripped. In ASCII, the control codes have decimal codes 0 through to 31 and 127. On an ASCII based system, if the control codes are stripped, the resultant string would have all of its characters within the range of 32 to 126 decimal on the ASCII table. On a non-ASCII based system, we consider characters that do not have a corresponding glyph on the ASCII table (within the ASCII range of 32 to 126 decimal) to be an extended character for the purpose of this task.

### Tests

1. `strip` should be a function.
2. `strip("abc")` should return a string.
3. `strip("\ba\x00b\n\rc\fd\xc3")` should return `"abcd"`.
4. `strip("\u0000\n abc\u00E9def\u007F")` should return `" abcdef"`.
5. `strip("a\n\tb\u2102d\u2147f")` should return `"abdf"`.
6. `strip("Français.")` should return `"Franais."`.
7. `strip("123\tabc\u0007DEF\u007F+-*/€æŧðłþ")` should return `"123abcDEF+-*/"`.

### Solution:

```javascript
function strip(str) {
    return str.replace(/[\x00-\x1F\x7F\u0080-\uFFFF]/g, '');
}
```