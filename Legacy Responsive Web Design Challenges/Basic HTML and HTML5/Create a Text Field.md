# Create a Text Field

### Description

Now let's create a web form.

`input` elements are a convenient way to get input from your user.

You can create a text `input` like this:

```html
<input type="text">
```

Note that `input` is a void element.

---

Create an `input` element of type text below your lists.

### Tests

1. Your app should have an `input` element of type `text`.

### Solution

```html
<h2>CatPhotoApp</h2>
<main>
  <p>Click here to view more <a href="#">cat photos</a>.</p>

  <a href="#"><img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back."></a>

  <p>Things cats love:</p>
  <ul>
    <li>catnip</li>
    <li>laser pointers</li>
    <li>lasagna</li>
  </ul>
  <p>Top 3 things cats hate:</p>
  <ol>
    <li>flea treatment</li>
    <li>thunder</li>
    <li>other cats</li>
  </ol>

  <input type="text">
</main>
```