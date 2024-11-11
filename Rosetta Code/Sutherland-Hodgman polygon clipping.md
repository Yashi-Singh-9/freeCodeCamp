# Sutherland-Hodgman polygon clipping

### Description

The Sutherland-Hodgman clipping algorithm finds the polygon that is the intersection between an arbitrary polygon (the "subject polygon") and a convex polygon (the "clip polygon"). It is used in computer graphics (especially 2D graphics) to reduce the complexity of a scene being displayed by eliminating parts of a polygon that do not need to be displayed. Take the closed polygon defined by the points:

[(50, 150), (200, 50), (350, 150), (350, 300), (250, 300), (200, 250), (150, 350), (100, 250), (100, 200)]
and clip it by the rectangle defined by the points:

[(100, 100), (300, 100), (300, 300), (100, 300)]

---

Write a function that takes 2 arrays as parameters. The first array contains the points of the subject polygon and the second array contains the points of the clipping polygon. The function should return an array containing the points of the clipped polygon. Each number should be rounded to 3 decimal places.

### Tests

1. `clip` should be a function.
2. `clip([[50, 150], [200, 50], [350, 150], [350, 300], [250, 300], [200, 250], [150, 350], [100, 250], [100, 200]], [[100, 100], [300, 100], [300, 300], [100, 300]])` should return an array.
3. `clip([[50, 150], [200, 50], [350, 150], [350, 300], [250, 300], [200, 250], [150, 350], [100, 250], [100, 200]], [[100, 100], [300, 100], [300, 300], [100, 300]])` should return `[[100, 116.667], [125, 100], [275, 100], [300, 116.667], [300, 300], [250, 300], [200, 250], [175, 300], [125, 300], [100, 250]]`.
4. `clip([[150, 200], [400, 450], [30, 50]], [[10, 10], [300, 200], [400, 600], [100, 300]])` should return `[[150, 200], [350, 400], [348.611, 394.444], [30, 50]]`.
5. `clip([[250, 200], [100, 450], [130, 250]], [[50, 60], [100, 230], [400, 600], [100, 300]])` should return `[[129.167, 329.167], [119.565, 319.565], [121.854, 304.305]]`.

### Solution

```javascript
function clip(subjectPolygon, clipPolygon) {
    // Helper function to calculate intersection between two lines
    function computeIntersection(p1, p2, cp1, cp2) {
        const x1 = p1[0], y1 = p1[1];
        const x2 = p2[0], y2 = p2[1];
        const x3 = cp1[0], y3 = cp1[1];
        const x4 = cp2[0], y4 = cp2[1];
        
        const denom = (x1 - x2) * (y3 - y4) - (y1 - y2) * (x3 - x4);
        if (denom === 0) return null;  // Lines are parallel or coincident
        
        const intersectX = ((x1 * y2 - y1 * x2) * (x3 - x4) - (x1 - x2) * (x3 * y4 - y3 * x4)) / denom;
        const intersectY = ((x1 * y2 - y1 * x2) * (y3 - y4) - (y1 - y2) * (x3 * y4 - y3 * x4)) / denom;
        
        return [intersectX, intersectY];
    }

    // Helper function to check if a point is inside the clipping boundary
    function inside(p, cp1, cp2) {
        return (cp2[0] - cp1[0]) * (p[1] - cp1[1]) > (cp2[1] - cp1[1]) * (p[0] - cp1[0]);
    }

    let output = subjectPolygon;

    for (let i = 0; i < clipPolygon.length; i++) {
        const cp1 = clipPolygon[i];
        const cp2 = clipPolygon[(i + 1) % clipPolygon.length];
        const newOutput = [];
        
        for (let j = 0; j < output.length; j++) {
            const current = output[j];
            const prev = output[(j - 1 + output.length) % output.length];
            
            // Check if the current point is inside the clipping boundary
            if (inside(current, cp1, cp2)) {
                if (!inside(prev, cp1, cp2)) {
                    // Compute intersection
                    const intersection = computeIntersection(prev, current, cp1, cp2);
                    if (intersection) {
                        newOutput.push(intersection);
                    }
                }
                newOutput.push(current);
            } else if (inside(prev, cp1, cp2)) {
                // Compute intersection
                const intersection = computeIntersection(prev, current, cp1, cp2);
                if (intersection) {
                    newOutput.push(intersection);
                }
            }
        }
        
        output = newOutput;
    }

    // Round the points to 3 decimal places
    return output.map(p => [parseFloat(p[0].toFixed(3)), parseFloat(p[1].toFixed(3))]);
}

// Test cases
console.log(clip([[50, 150], [200, 50], [350, 150], [350, 300], [250, 300], [200, 250], [150, 350], [100, 250], [100, 200]], [[100, 100], [300, 100], [300, 300], [100, 300]]));
console.log(clip([[150, 200], [400, 450], [30, 50]], [[10, 10], [300, 200], [400, 600], [100, 300]]));
console.log(clip([[250, 200], [100, 450], [130, 250]], [[50, 60], [100, 230], [400, 600], [100, 300]]));
```