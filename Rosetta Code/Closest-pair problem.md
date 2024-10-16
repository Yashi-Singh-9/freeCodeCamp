# Closest-pair problem

Provide a function to find the closest two points among a set of given points in two dimensions.

The straightforward solution is a  O(n<sup>2</sup>) algorithm (which we can call brute-force algorithm); the pseudo-code (using indexes) could be simply:

```
bruteForceClosestPair of P(1), P(2), ... P(N)
if N < 2 then
  return ∞
else
  minDistance ← |P(1) - P(2)|
  minPoints ← { P(1), P(2) }
  foreach i ∈ [1, N-1]
    foreach j ∈ [i+1, N]
      if |P(i) - P(j)| < minDistance then
        minDistance ← |P(i) - P(j)|
        minPoints ← { P(i), P(j) }
      endif
    endfor
  endfor
  return minDistance, minPoints
endif
```

A better algorithm is based on the recursive divide and conquer approach, which is  O(n log n) a pseudo-code could be:
```
closestPair of (xP, yP)
  where xP is P(1) .. P(N) sorted by x coordinate, and
  yP is P(1) .. P(N) sorted by y coordinate (ascending order)
if N ≤ 3 then
  return closest points of xP using brute-force algorithm
else
  xL ← points of xP from 1 to ⌈N/2⌉
  xR ← points of xP from ⌈N/2⌉+1 to N
  xm ← xP(⌈N/2⌉)x
  yL ← { p ∈ yP : px ≤ xm }
  yR ← { p ∈ yP : px > xm }
  (dL, pairL) ← closestPair of (xL, yL)
  (dR, pairR) ← closestPair of (xR, yR)
  (dmin, pairMin) ← (dR, pairR)
  if dL < dR then
    (dmin, pairMin) ← (dL, pairL)
  endif
  yS ← { p ∈ yP : |xm - px| < dmin }
  nS ← number of points in yS
  (closest, closestPair) ← (dmin, pairMin)
  for i from 1 to nS - 1
    k ← i + 1
    while k ≤ nS and yS(k)y - yS(i)y < dmin
      if |yS(k) - yS(i)| < closest then
        (closest, closestPair) ← (|yS(k) - yS(i)|, {yS(k), yS(i)})
      endif
      k ← k + 1
    endwhile
  endfor
  return closest, closestPair
endif
```

For the input, expect the argument to be an array of `Point` objects with `x` and `y` members set to numbers. Return an object containing the key:value pairs for `distance` and `pair` (the pair of two closest points).

For example `getClosestPair` with input array `points`:
```
const points = [
  new Point(1, 2),
  new Point(3, 3),
  new Point(2, 2)
];
```

Would return:
```
{
  distance: 1,
  pair: [
    {
      x: 1,
      y: 2
    },
    {
      x: 2,
      y: 2
    }
  ]
}
```

Note: Sort the `pair` array by their `x` values in incrementing order.

### Tests

1. `getClosestPair` should be a function.
2. `getClosestPair(points1).distance` should be `0.0894096443343775`.
3. `getClosestPair(points1).pair` should be `[ { x: 7.46489, y: 4.6268 }, { x: 7.46911, y: 4.71611 } ]`.
4. `getClosestPair(points2).distance` should be `65.06919393998976`.
5. `getClosestPair(points2).pair` should be `[ { x: 37134, y: 1963 }, { x: 37181, y: 2008 } ]`.
6. `getClosestPair(points3).distance` should be `6754.625082119658`.
7. `getClosestPair(points3).pair` should be `[ { x: 46817, y: 64975 }, { x: 48953, y: 58567 } ]`.

### Answer: 

```javascript
class Point {
    constructor(x, y) {
        this.x = x;
        this.y = y;
    }
}

function distance(point1, point2) {
    return Math.sqrt(Math.pow(point1.x - point2.x, 2) + Math.pow(point1.y - point2.y, 2));
}

function bruteForceClosestPair(points) {
    let minDistance = Infinity;
    let minPair = [];

    for (let i = 0; i < points.length - 1; i++) {
        for (let j = i + 1; j < points.length; j++) {
            const d = distance(points[i], points[j]);
            if (d < minDistance) {
                minDistance = d;
                minPair = [points[i], points[j]];
            }
        }
    }
    return { distance: minDistance, pair: minPair };
}

function closestPair(xP, yP) {
    const N = xP.length;

    // Base case: Use brute force for small number of points
    if (N <= 3) {
        return bruteForceClosestPair(xP);
    }

    const midIndex = Math.floor(N / 2);
    const midPoint = xP[midIndex];

    // Split points into left and right subsets
    const xL = xP.slice(0, midIndex);
    const xR = xP.slice(midIndex);
    const yL = yP.filter(point => point.x <= midPoint.x);
    const yR = yP.filter(point => point.x > midPoint.x);

    const leftResult = closestPair(xL, yL);
    const rightResult = closestPair(xR, yR);

    let minDistance = leftResult.distance;
    let minPair = leftResult.pair;

    if (rightResult.distance < minDistance) {
        minDistance = rightResult.distance;
        minPair = rightResult.pair;
    }

    // Create strip (points within minDistance of the middle line)
    const strip = yP.filter(point => Math.abs(point.x - midPoint.x) < minDistance);
    const stripSize = strip.length;

    for (let i = 0; i < stripSize; i++) {
        for (let j = i + 1; j < stripSize && (strip[j].y - strip[i].y) < minDistance; j++) {
            const d = distance(strip[i], strip[j]);
            if (d < minDistance) {
                minDistance = d;
                minPair = [strip[i], strip[j]];
            }
        }
    }

    return { distance: minDistance, pair: minPair };
}

function getClosestPair(points) {
    const xP = [...points].sort((a, b) => a.x - b.x);
    const yP = [...points].sort((a, b) => a.y - b.y);

    const result = closestPair(xP, yP);
    
    // Sort pair by their x values in increasing order
    result.pair.sort((a, b) => a.x - b.x);
    
    return {
        distance: result.distance,
        pair: result.pair.map(p => ({ x: p.x, y: p.y }))
    };
}

// Example usage:
const points1 = [
    new Point(1, 2),
    new Point(3, 3),
    new Point(2, 2)
];

const points2 = [
    new Point(37134, 1963),
    new Point(37181, 2008),
    // Add more points as needed...
];

const points3 = [
    new Point(46817, 64975),
    new Point(48953, 58567),
    // Add more points as needed...
];

// Testing the function with the provided points
console.log(getClosestPair(points1));
console.log(getClosestPair(points2));
console.log(getClosestPair(points3));
```