# Knapsack problem/Bounded

### Description

The bounded knapsack problem is defined as follows:

You are given an array of objects representing items to be put in a knapsack. The objects have 4 attributes: name, pieces (the number of the particular item), weight, and value. The items need to be selected so that the total weight does not exceed the maximum weight and the value is maximized. Keep in mind that each item can appear between 0 and `pieces` times.

---

Write a function to solve the knapsack problem. The function is given the array of objects and the maximum weight as parameters. It should return the maximum total value possible.

### Tests

1. `findBestPack([{ name:'map', weight:9, value:150, pieces:1 }, { name:'compass', weight:13, value:35, pieces:1 }, { name:'water', weight:153, value:200, pieces:2 }, { name:'sandwich', weight:50, value:60, pieces:2 }, { name:'glucose', weight:15, value:60, pieces:2 }, { name:'tin', weight:68, value:45, pieces:3 }, { name:'banana', weight:27, value:60, pieces:3 }, { name:'apple', weight:39, value:40, pieces:3 }, { name:'cheese', weight:23, value:30, pieces:1 }, { name:'beer', weight:52, value:10, pieces:3 }, { name:'suntan, cream', weight:11, value:70, pieces:1 }, { name:'camera', weight:32, value:30, pieces:1 }, { name:'T-shirt', weight:24, value:15, pieces:2 }], 300)` should return `755`.

2. `findBestPack([{ name:'map', weight:9, value:150, pieces:1 }, { name:'compass', weight:13, value:35, pieces:1 }, { name:'water', weight:153, value:200, pieces:2 }, { name:'sandwich', weight:50, value:60, pieces:2 }, { name:'glucose', weight:15, value:60, pieces:2 }, { name:'tin', weight:68, value:45, pieces:3 }, { name:'banana', weight:27, value:60, pieces:3 }, { name:'apple', weight:39, value:40, pieces:3 }, { name:'cheese', weight:23, value:30, pieces:1 }, { name:'beer', weight:52, value:10, pieces:3 }, { name:'suntan, cream', weight:11, value:70, pieces:1 }, { name:'camera', weight:32, value:30, pieces:1 }, { name:'T-shirt', weight:24, value:15, pieces:2 }], 400)` should return `875`.

3. `findBestPack([{ name:'map', weight:9, value:150, pieces:1 }, { name:'compass', weight:13, value:35, pieces:1 }, { name:'water', weight:153, value:200, pieces:2 }, { name:'sandwich', weight:50, value:60, pieces:2 }, { name:'glucose', weight:15, value:60, pieces:2 }, { name:'tin', weight:68, value:45, pieces:3 }, { name:'banana', weight:27, value:60, pieces:3 }, { name:'apple', weight:39, value:40, pieces:3 }, { name:'cheese', weight:23, value:30, pieces:1 }, { name:'beer', weight:52, value:10, pieces:3 }, { name:'suntan, cream', weight:11, value:70, pieces:1 }, { name:'camera', weight:32, value:30, pieces:1 }, { name:'T-shirt', weight:24, value:15, pieces:2 }], 500)` should return `1015`.

4. `findBestPack([{ name:'map', weight:9, value:150, pieces:1 }, { name:'compass', weight:13, value:35, pieces:1 }, { name:'water', weight:153, value:200, pieces:2 }, { name:'sandwich', weight:50, value:60, pieces:2 }, { name:'glucose', weight:15, value:60, pieces:2 }, { name:'tin', weight:68, value:45, pieces:3 }, { name:'banana', weight:27, value:60, pieces:3 }, { name:'apple', weight:39, value:40, pieces:3 }, { name:'cheese', weight:23, value:30, pieces:1 }, { name:'beer', weight:52, value:10, pieces:3 }, { name:'suntan, cream', weight:11, value:70, pieces:1 }, { name:'camera', weight:32, value:30, pieces:1 }, { name:'T-shirt', weight:24, value:15, pieces:2 }], 600)` should return `1120`.

5. `findBestPack([{ name:'map', weight:9, value:150, pieces:1 }, { name:'compass', weight:13, value:35, pieces:1 }, { name:'water', weight:153, value:200, pieces:2 }, { name:'sandwich', weight:50, value:60, pieces:2 }, { name:'glucose', weight:15, value:60, pieces:2 }, { name:'tin', weight:68, value:45, pieces:3 }, { name:'banana', weight:27, value:60, pieces:3 }, { name:'apple', weight:39, value:40, pieces:3 }, { name:'cheese', weight:23, value:30, pieces:1 }, { name:'beer', weight:52, value:10, pieces:3 }, { name:'suntan, cream', weight:11, value:70, pieces:1 }, { name:'camera', weight:32, value:30, pieces:1 }, { name:'T-shirt', weight:24, value:15, pieces:2 }], 700)` should return `1225`.

### Answer:

```javascript
function findBestPack(items, maxWeight) {
    // Create an array to store the maximum value at each capacity
    const dp = new Array(maxWeight + 1).fill(0);

    // Iterate over each item
    for (const item of items) {
        const { weight, value, pieces } = item;

        // For each piece of the item
        for (let p = 1; p <= pieces; p++) {
            // We iterate backward to avoid overwriting results
            for (let w = maxWeight; w >= weight; w--) {
                dp[w] = Math.max(dp[w], dp[w - weight] + value);
            }
        }
    }

    // The maximum value is found in dp[maxWeight]
    return dp[maxWeight];
}

// Test cases
console.log(findBestPack([
    { name: 'map', weight: 9, value: 150, pieces: 1 },
    { name: 'compass', weight: 13, value: 35, pieces: 1 },
    { name: 'water', weight: 153, value: 200, pieces: 2 },
    { name: 'sandwich', weight: 50, value: 60, pieces: 2 },
    { name: 'glucose', weight: 15, value: 60, pieces: 2 },
    { name: 'tin', weight: 68, value: 45, pieces: 3 },
    { name: 'banana', weight: 27, value: 60, pieces: 3 },
    { name: 'apple', weight: 39, value: 40, pieces: 3 },
    { name: 'cheese', weight: 23, value: 30, pieces: 1 },
    { name: 'beer', weight: 52, value: 10, pieces: 3 },
    { name: 'suntan cream', weight: 11, value: 70, pieces: 1 },
    { name: 'camera', weight: 32, value: 30, pieces: 1 },
    { name: 'T-shirt', weight: 24, value: 15, pieces: 2 }
], 300)); // Output: 755

console.log(findBestPack([
    { name: 'map', weight: 9, value: 150, pieces: 1 },
    { name: 'compass', weight: 13, value: 35, pieces: 1 },
    { name: 'water', weight: 153, value: 200, pieces: 2 },
    { name: 'sandwich', weight: 50, value: 60, pieces: 2 },
    { name: 'glucose', weight: 15, value: 60, pieces: 2 },
    { name: 'tin', weight: 68, value: 45, pieces: 3 },
    { name: 'banana', weight: 27, value: 60, pieces: 3 },
    { name: 'apple', weight: 39, value: 40, pieces: 3 },
    { name: 'cheese', weight: 23, value: 30, pieces: 1 },
    { name: 'beer', weight: 52, value: 10, pieces: 3 },
    { name: 'suntan cream', weight: 11, value: 70, pieces: 1 },
    { name: 'camera', weight: 32, value: 30, pieces: 1 },
    { name: 'T-shirt', weight: 24, value: 15, pieces: 2 }
], 400)); // Output: 875

console.log(findBestPack([
    { name: 'map', weight: 9, value: 150, pieces: 1 },
    { name: 'compass', weight: 13, value: 35, pieces: 1 },
    { name: 'water', weight: 153, value: 200, pieces: 2 },
    { name: 'sandwich', weight: 50, value: 60, pieces: 2 },
    { name: 'glucose', weight: 15, value: 60, pieces: 2 },
    { name: 'tin', weight: 68, value: 45, pieces: 3 },
    { name: 'banana', weight: 27, value: 60, pieces: 3 },
    { name: 'apple', weight: 39, value: 40, pieces: 3 },
    { name: 'cheese', weight: 23, value: 30, pieces: 1 },
    { name: 'beer', weight: 52, value: 10, pieces: 3 },
    { name: 'suntan cream', weight: 11, value: 70, pieces: 1 },
    { name: 'camera', weight: 32, value: 30, pieces: 1 },
    { name: 'T-shirt', weight: 24, value: 15, pieces: 2 }
], 500)); // Output: 1015

console.log(findBestPack([
    { name: 'map', weight: 9, value: 150, pieces: 1 },
    { name: 'compass', weight: 13, value: 35, pieces: 1 },
    { name: 'water', weight: 153, value: 200, pieces: 2 },
    { name: 'sandwich', weight: 50, value: 60, pieces: 2 },
    { name: 'glucose', weight: 15, value: 60, pieces: 2 },
    { name: 'tin', weight: 68, value: 45, pieces: 3 },
    { name: 'banana', weight: 27, value: 60, pieces: 3 },
    { name: 'apple', weight: 39, value: 40, pieces: 3 },
    { name: 'cheese', weight: 23, value: 30, pieces: 1 },
    { name: 'beer', weight: 52, value: 10, pieces: 3 },
    { name: 'suntan cream', weight: 11, value: 70, pieces: 1 },
    { name: 'camera', weight: 32, value: 30, pieces: 1 },
    { name: 'T-shirt', weight: 24, value: 15, pieces: 2 }
], 600)); // Output: 1120

console.log(findBestPack([
    { name: 'map', weight: 9, value: 150, pieces: 1 },
    { name: 'compass', weight: 13, value: 35, pieces: 1 },
    { name: 'water', weight: 153, value: 200, pieces: 2 },
    { name: 'sandwich', weight: 50, value: 60, pieces: 2 },
    { name: 'glucose', weight: 15, value: 60, pieces: 2 },
    { name: 'tin', weight: 68, value: 45, pieces: 3 },
    { name: 'banana', weight: 27, value: 60, pieces: 3 },
    { name: 'apple', weight: 39, value: 40, pieces: 3 },
    { name: 'cheese', weight: 23, value: 30, pieces: 1 },
    { name: 'beer', weight: 52, value: 10, pieces: 3 },
    { name: 'suntan cream', weight: 11, value: 70, pieces: 1 },
    { name: 'camera', weight: 32, value: 30, pieces: 1 },
    { name: 'T-shirt', weight: 24, value: 15, pieces: 2 }
], 700)); // Output: 1225
```