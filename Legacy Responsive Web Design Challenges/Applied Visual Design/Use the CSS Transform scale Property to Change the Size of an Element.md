# Use the CSS Transform scale Property to Change the Size of an Element

### Description

To change the scale of an element, CSS has the `transform` property, along with its `scale()` function. The following code example doubles the size of all the paragraph elements on the page:

```css
p {
  transform: scale(2);
}
```
---

Increase the size of the element with the id of `ball2` to 1.5 times its original size.

### Tests

1. The `transform` property for `#ball2` should be set to scale it to 1.5 times its size.

### Solution

```html
<style>
  .ball {
    width: 40px;
    height: 40px;
    margin: 50 auto;
    position: fixed;
    background: linear-gradient(
      35deg,
      #ccffff,
      #ffcccc
    );
    border-radius: 50%;
  }
  #ball1 {
    left: 20%;
  }
  #ball2 {
    left: 65%;
    transform: scale(1.5);
  }


</style>

<div class="ball" id= "ball1"></div>
<div class="ball" id= "ball2"></div>
```