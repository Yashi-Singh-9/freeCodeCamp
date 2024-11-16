# Inherit Styles from the Body Element

### Description

Now we've proven that every HTML page has a `body` element, and that its `body` element can also be styled with CSS.

Remember, you can style your `body` element just like any other HTML element, and all your other elements will inherit your `body` element's styles.

---

First, create an `h1` element with the text `Hello World`.

Then, let's give all elements on your page the color of `green` by adding `color: green;` to your `body` element's style declaration.

Finally, give your `body` element the font-family of `monospace` by adding `font-family: monospace;` to your `body` element's style declaration.

### Tests

1. You should create an `h1` element.
2. Your `h1` element should have the text `Hello World`.
3. Your `h1` element should have a closing tag.
4. Your `body` element should have the `color` property of `green`.
5. Your `body` element should have the `font-family` property of `monospace`.
6. Your `h1` element should inherit the font `monospace` from your `body` element.
7. Your `h1` element should inherit the color `green` from your `body` element.

### Solution

```html
<style>
  body {
    background-color: black;
    color: green;
    font-family: monospace;
  }
</style>

<h1> Hello World </h1>
```