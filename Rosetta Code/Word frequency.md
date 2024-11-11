# Word frequency

### Description

Given a text string and an integer n, return the n most common words in the file (and the number of their occurrences) in decreasing frequency.

---

Write a function to count the occurrences of each word and return the n most commons words along with the number of their occurrences in decreasing frequency.

The function should return a 2D array with each of the elements in the following form: `[word, freq]`. `word` should be the lowercase version of the word and `freq` the number denoting the count.

The function should return an empty array, if no string is provided.

The function should be case insensitive, for example, the strings "Hello" and "hello" should be treated the same.

You can treat words that have special characters such as underscores, dashes, apostrophes, commas, etc., as distinct words.

For example, given the string "Hello hello goodbye", your function should return `[['hello', 2], ['goodbye', 1]]`.

### Tests

1. `wordFrequency` should be a function.
2. `wordFrequency` should return an array.
3. `wordFrequency("Hello hello world", 2)` should return `[['hello', 2], ['world', 1]]`
4. `wordFrequency("The quick brown fox jumped over the lazy dog", 1)` should return `[['the', 2]]`
5. `wordFrequency("Opensource opensource open-source open source", 1)` should return `[['opensource', 2]]`
6. `wordFrequency("Apple App apply aPP aPPlE", 3)` should return `[['app', 2], ['apple', 2], ['apply', 1]] or [['apple', 2], ['app', 2], ['apply', 1]]`
7. `wordFrequency("c d a d c a b d d c", 4)` should return `[['d', 4], ['c', 3], ['a', 2], ['b', 1]]`
8. `wordFrequency("", 5)` should return `[]`

### Solution

```javascript
function wordFrequency(text, n) {
    // Return an empty array if no text is provided
    if (!text) {
        return [];
    }
    
    // Convert the text to lowercase and split it into words
    let words = text.toLowerCase().split(/\s+/);

    // Create a frequency map for the words
    let frequencyMap = {};

    words.forEach(word => {
        frequencyMap[word] = (frequencyMap[word] || 0) + 1;
    });

    // Convert the frequency map into an array of [word, freq] pairs
    let frequencyArray = Object.entries(frequencyMap);

    // Sort the array by frequency in decreasing order, and then alphabetically for ties
    frequencyArray.sort((a, b) => b[1] - a[1] || a[0].localeCompare(b[0]));

    // Return the top 'n' most common words
    return frequencyArray.slice(0, n);
}

// Example tests
console.log(wordFrequency("Hello hello world", 2)); // [['hello', 2], ['world', 1]]
console.log(wordFrequency("The quick brown fox jumped over the lazy dog", 1)); // [['the', 2]]
console.log(wordFrequency("Opensource opensource open-source open source", 1)); // [['opensource', 2]]
console.log(wordFrequency("Apple App apply aPP aPPlE", 3)); // [['app', 2], ['apple', 2], ['apply', 1]]
console.log(wordFrequency("c d a d c a b d d c", 4)); // [['d', 4], ['c', 3], ['a', 2], ['b', 1]]
console.log(wordFrequency("", 5)); // []
```