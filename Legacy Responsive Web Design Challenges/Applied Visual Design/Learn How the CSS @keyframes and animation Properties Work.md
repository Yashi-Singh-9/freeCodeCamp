# Learn How the CSS @keyframes and animation Properties Work

### Description

To animate an element, you need to know about the animation properties and the `@keyframes` rule. The animation properties control how the animation should behave and the `@keyframes` rule controls what happens during that animation. There are eight animation properties in total. This challenge will keep it simple and cover the two most important ones first:

`animation-name` sets the name of the animation, which is later used by `@keyframes` to tell CSS which rules go with which animations.

`animation-duration` sets the length of time for the animation.

`@keyframes` is how to specify exactly what happens within the animation over the duration. This is done by giving CSS properties for specific "frames" during the animation, with percentages ranging from 0% to 100%. If you compare this to a movie, the CSS properties for 0% is how the element displays in the opening scene. The CSS properties for 100% is how the element appears at the end, right before the credits roll. Then CSS applies the magic to transition the element over the given duration to act out the scene. Here's an example to illustrate the usage of `@keyframes` and the animation properties:

```css
#anim {
  animation-name: colorful;
  animation-duration: 3s;
}

@keyframes colorful {
  0% {
    background-color: blue;
  }
  100% {
    background-color: yellow;
  }
}
```

For the element with the `anim` id, the code snippet above sets the `animation-name` to `colorful` and sets the `animation-duration` to 3 seconds. Then the `@keyframes` rule links to the animation properties with the name `colorful`. It sets the color to blue at the beginning of the animation (0%) which will transition to yellow by the end of the animation (100%). You aren't limited to only beginning-end transitions, you can set properties for the element for any percentage between 0% and 100%.

---

Create an animation for the element with the id `rect`, by setting the `animation-name` to `rainbow` and the `animation-duration` to 4 seconds. Next, declare a `@keyframes` rule, and set the `background-color` at the beginning of the animation (`0%`) to blue, the middle of the animation (`50%`) to green, and the end of the animation (`100%`) to yellow.

### Tests

1. The element with id of `rect` should have an `animation-name` property with a value of `rainbow`.
2. The element with id of `rect` should have an `animation-duration` property with a value of 4s.
3. The `@keyframes` rule should use the `animation-name` of `rainbow`.
4. The `@keyframes` rule for `rainbow` should use a `background-color` of `blue` at 0%.
5. The `@keyframes` rule for `rainbow` should use a `background-color` of `green` at 50%.
6. The `@keyframes` rule for rainbow should use a `background-color` of `yellow` at 100%.

### Solution

```html
<style>
  div {
    height: 40px;
    width: 70%;
    background: black;
    margin: 50px auto;
    border-radius: 5px;
  }

  #rect {
    animation-name: rainbow;
    animation-duration: 4s;
  }

  @keyframes rainbow {
    0% {
      background-color: blue;
    }
    50% {
      background-color: green;
    }
    100% {
      background-color: yellow;
    }
  }
</style>

<div id="rect"></div>
```