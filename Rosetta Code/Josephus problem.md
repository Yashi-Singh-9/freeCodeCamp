# Josephus problem

### Description

Josephus problem is a math puzzle with a grim description: $n$ prisoners are standing on a circle, sequentially numbered from $0$ to $n-1$.

An executioner walks along the circle, starting from prisoner $0$, removing every $k$-th prisoner and killing him.

As the process goes on, the circle becomes smaller and smaller, until only one prisoner remains, who is then freed.

For example, if there are $n=5$ prisoners and $k=2$, the order the prisoners are killed in (let's call it the "killing sequence") will be 1, 3, 0, and 4, and the survivor will be #2.

Given any $n, k > 0$, find out which prisoner will be the final survivor.

In one such incident, there were 41 prisoners and every 3rd prisoner was being killed ($k=3$).

Among them was a clever chap name Josephus who worked out the problem, stood at the surviving position, and lived on to tell the tale.

Which number was he?

Write a function that takes the initial number of prisoners and `k` as parameters and returns the number of the prisoner that survives.

### Tests 

1. `josephus` should be a function.
2. `josephus(30,3)` should return a number.
3. `josephus(30,3)` should return `28`.
4. `josephus(30,5)` should return `2`.
5. `josephus(20,2)` should return `8`.
6. `josephus(17,6)` should return `1`.
7. `josephus(29,4)` should return `1`.

### Answer:

```javascript
function josephus(n, k) {
    let survivor = 0; // Base case: J(1, k) = 0
    for (let i = 2; i <= n; i++) {
        survivor = (survivor + k) % i;
    }
    return survivor; // Returns zero-based index
}

// Example usage
const n = 41;
const k = 3;
const survivorPosition = josephus(n, k);
console.log(`The survivor is prisoner number: ${survivorPosition}`);
```