# Babbage problem

### Description

Charles Babbage, looking ahead to the sorts of problems his Analytical Engine would be able to solve, gave this example:

> What is the smallest positive integer whose square ends in the digits 269,696? <p> Babbage, letter to Lord Bowden, 1837; see Hollingdale and Tootill, Electronic Computers, second edition, 1970, p. 125.</p>

He thought the answer might be 99,736, whose square is 9,947,269,696; but he couldn't be certain.

The task is to find out if Babbage had the right answer.

---

Implement a function to return the lowest integer that satisfies the Babbage problem. If Babbage was right, return Babbage's number.

---

### Tests

1. `babbage` should be a function.
2. `babbage(99736, 269696)` should not return 99736 (there is a smaller answer).

### Answer:

```javascript
function isBabbage(testVal, endDigits) {
  const endStr = '' + endDigits;
  const squareStr = ('' + Math.pow(testVal, 2))
    .slice(-endStr.length);
  return endStr === squareStr;
}

function babbage(babbageNum, endDigits) {
  const start = Math.floor(Math.sqrt(endDigits));
  for (let i = start; i <= babbageNum; i++)
    if (isBabbage(i, endDigits))
      return i;
}

console.log(babbage(99736, 269696));
```