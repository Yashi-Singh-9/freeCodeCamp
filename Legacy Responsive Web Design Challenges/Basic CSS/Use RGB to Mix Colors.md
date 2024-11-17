# Use RGB to Mix Colors

### Description

Just like with hex code, you can mix colors in RGB by using combinations of different values.

---

Replace the hex codes in our `style` element with their correct RGB values.

```
Color	                    RGB
Blue	                rgb(0, 0, 255)
Red	                rgb(255, 0, 0)
Orchid	                rgb(218, 112, 214)
Sienna	                rgb(160, 82, 45)
```

### Tests

1. Your `h1` element with the text `I am red!` should have the `color` red.
2. You should use `rgb` for the color red.
3. Your `h1` element with the text `I am orchid!` should have the `color` orchid.
4. You should use rgb for the `color` orchid.
5. Your `h1` element with the text `I am blue!` should have the `color` blue.
6. You should use `rgb` for the color blue.
7. Your `h1` element with the text `I am sienna!` should have the `color` sienna.
8. You should use `rgb` for the color sienna.

### Solution

```html
<style>
  .red-text {
    color: rgb(255, 0, 0);
  }
  .orchid-text {
    color: rgb(218, 112, 214);
  }
  .sienna-text {
    color: rgb(160, 82, 45);
  }
  .blue-text {
    color: rgb(0, 0, 255);
  }
</style>

<h1 class="red-text">I am red!</h1>

<h1 class="orchid-text">I am orchid!</h1>

<h1 class="sienna-text">I am sienna!</h1>

<h1 class="blue-text">I am blue!</h1>
```