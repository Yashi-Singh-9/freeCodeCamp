# Create a Form Element

### Description

You can build web forms that actually submit data to a server using nothing more than pure HTML. You can do this by specifying an `action` attribute on your `form` element.

For example:

```html
<form action="url-where-you-want-to-submit-form-data">
  <input>
</form>
```

Nest the existing `input` element inside a `form` element and assign `"https://www.freecatphotoapp.com/submit-cat-photo"` to the `action` attribute of the `form` element.

### Tests

1. The existing `input` element should be nested within a `form` element.
2. Your form should have an action attribute which is set to https://www.freecatphotoapp.com/submit-cat-photo.
3. Your form element should have well-formed open and close tags.

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
  <form action="https://www.freecatphotoapp.com/submit-cat-photo">
  <input type="text" placeholder="cat photo URL">
  </form>
</main>
```