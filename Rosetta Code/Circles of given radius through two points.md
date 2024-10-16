# Circles of given radius through two points

Given two points on a plane and a radius, usually two circles of given radius can be drawn through the points.

Exceptions:

- A radius of zero should be treated as never describing circles (except in the case where the points are coincident).
- If the points are coincident then an infinite number of circles with the point on their circumference can be drawn, unless the radius is equal to zero as well which then collapses the circles to a point.
- If the points form a diameter then return a single circle.
- If the points are too far apart then no circles can be drawn.

---

Implement a function that takes two points and a radius and returns the two circles through those points. For each resulting circle, provide the coordinates for the center of each circle rounded to four decimal digits. Return each coordinate as an array, and coordinates as an array of arrays.

For edge cases, return the following:

- If points are on the diameter, return one point. If the radius is also zero however, return `"Radius Zero"`.
- If points are coincident, return "`Coincident point. Infinite solutions"`.
- If points are farther apart than the diameter, return `"No intersection. Points further apart than circle diameter"`.

Sample inputs:
```
      p1                p2           r
0.1234, 0.9876    0.8765, 0.2345    2.0
0.0000, 2.0000    0.0000, 0.0000    1.0
0.1234, 0.9876    0.1234, 0.9876    2.0
0.1234, 0.9876    0.8765, 0.2345    0.5
0.1234, 0.9876    0.1234, 0.9876    0.0
```

### Tests

1. `getCircles` should be a function.
2. `getCircles([0.1234, 0.9876], [0.8765, 0.2345], 2.0)` should return `[[1.8631, 1.9742], [-0.8632, -0.7521]]`.
3. `getCircles([0.0000, 2.0000], [0.0000, 0.0000], 1.0)` should return `[0, 1]`
4. `getCircles([0.1234, 0.9876], [0.1234, 0.9876], 2.0)` should return `Coincident point. Infinite solutions`
5. `getCircles([0.1234, 0.9876], [0.8765, 0.2345], 0.5)` should return `No intersection. Points further apart than circle diameter`
6. `getCircles([0.1234, 0.9876], [0.1234, 0.9876], 0.0)` should return `Radius Zero`

### Answer:

```javascript
function getCircles(p1, p2, r) {
    // Destructure the points
    const [x1, y1] = p1;
    const [x2, y2] = p2;

    // Calculate distance between the points
    const distance = Math.sqrt((x2 - x1) ** 2 + (y2 - y1) ** 2);

    // Case 1: Coincident Points
    if (distance === 0) {
        return r === 0 ? "Radius Zero" : "Coincident point. Infinite solutions";
    }

    // Case 2: Points too far apart
    if (distance > 2 * r) {
        return "No intersection. Points further apart than circle diameter";
    }

    // Case 3: Points form a diameter
    if (distance === 2 * r) {
        const midpoint = [(x1 + x2) / 2, (y1 + y2) / 2];
        return [parseFloat(midpoint[0].toFixed(4)), parseFloat(midpoint[1].toFixed(4))];
    }

    // Case 4: General case, find two circle centers
    // Midpoint between p1 and p2
    const midpoint = [(x1 + x2) / 2, (y1 + y2) / 2];

    // Distance from the midpoint to either of the two circle centers
    const d = Math.sqrt(r ** 2 - (distance / 2) ** 2);

    // Unit vector perpendicular to the line between p1 and p2
    const dx = (x2 - x1) / distance;
    const dy = (y2 - y1) / distance;
    const perpDx = -dy;
    const perpDy = dx;

    // Two possible centers
    const center1 = [midpoint[0] + d * perpDx, midpoint[1] + d * perpDy];
    const center2 = [midpoint[0] - d * perpDx, midpoint[1] - d * perpDy];

    // Round the coordinates to four decimal digits
    return [
        [parseFloat(center1[0].toFixed(4)), parseFloat(center1[1].toFixed(4))],
        [parseFloat(center2[0].toFixed(4)), parseFloat(center2[1].toFixed(4))]
    ];
}

// Sample test cases
console.log(getCircles([0.1234, 0.9876], [0.8765, 0.2345], 2.0)); // Expected: [[1.8631, 1.9742], [-0.8632, -0.7521]]
console.log(getCircles([0.0000, 2.0000], [0.0000, 0.0000], 1.0)); // Expected: [0, 1]
console.log(getCircles([0.1234, 0.9876], [0.1234, 0.9876], 2.0)); // Expected: "Coincident point. Infinite solutions"
console.log(getCircles([0.1234, 0.9876], [0.8765, 0.2345], 0.5)); // Expected: "No intersection. Points further apart than circle diameter"
console.log(getCircles([0.1234, 0.9876], [0.1234, 0.9876], 0.0)); // Expected: "Radius Zero"
```