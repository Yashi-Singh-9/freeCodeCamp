# Override All Other Styles by using Important

### Description

Yay! We just proved that inline styles will override all the CSS declarations in your `style` element.

But wait. There's one last way to override CSS. This is the most powerful method of all. But before we do it, let's talk about why you would ever want to override CSS.

In many situations, you will use CSS libraries. These may accidentally override your own CSS. So when you absolutely need to be sure that an element has specific CSS, you can use `!important`.

Let's go all the way back to our `pink-text` class declaration. Remember that our `pink-text` class was overridden by subsequent class declarations, id declarations, and inline styles.

---

Let's add the keyword `!important` to your pink-text element's color declaration to make 100% sure that your `h1` element will be pink.

An example of how to do this is:

```css
color: red !important;
```
### Tests

1. Your `h1` element should have the class `pink-text`.
2. Your `h1` element should have the class `blue-text`.
3. Your `h1` element should have the `id` of `orange-text`.
4. Your `h1` element should have the inline style of `color: white`.
5. Your `pink-text` class declaration should have the `!important` keyword to override all other declarations.
6. Your `h1` element should be pink.

### Solution

```html
<style>
  body {
    background-color: black;
    font-family: monospace;
    color: green;
  }
  #orange-text {
    color: orange;
  }
  .pink-text {
    color: pink !important;
  }
  .blue-text {
    color: blue;
  }
</style>
<h1 id="orange-text" class="pink-text blue-text" style="color: white">Hello World!</h1>
```