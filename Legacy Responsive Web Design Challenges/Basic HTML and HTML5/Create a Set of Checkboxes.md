# Create a Set of Checkboxes

Forms commonly use *checkboxes* for questions that may have more than one answer.

Checkboxes are a type of `input`.

Each of your checkboxes can be nested within its own `label` element. By wrapping an `input` element inside of a `label` element it will automatically associate the checkbox input with the label element surrounding it.

All related checkbox inputs should have the same `name` attribute.

It is considered best practice to explicitly define the relationship between a checkbox `input` and its corresponding `label` by setting the `for` attribute on the `label` element to match the `id` attribute of the associated input element.

Here's an example of a checkbox:

```html
<label for="loving"><input id="loving" type="checkbox" name="personality"> Loving</label>
```

---

Add to your form a set of three checkboxes. Each checkbox should be nested within its own `label` element. All three should share the `name` attribute of `personality`.

### Tests

1. Your page should have three checkbox elements.
2. Each of your three checkbox elements should be nested in its own `label` element.
3. Make sure each of your `label` elements has a closing tag.
4. Your checkboxes should be given the `name` attribute of `personality`.
5. Each of your checkboxes should be added within the `form` tag.

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
    <label for="indoor"><input id="indoor" type="radio" name="indoor-outdoor"> Indoor</label>
    <label for="outdoor"><input id="outdoor" type="radio" name="indoor-outdoor"> Outdoor</label><br>
    <input type="text" placeholder="cat photo URL" required>
    <button type="submit">Submit</button>

    <!-- New checkbox section -->
    <p>What personality traits does your cat have?</p>
    <label for="loving"><input id="loving" type="checkbox" name="personality"> Loving</label><br>
    <label for="playful"><input id="playful" type="checkbox" name="personality"> Playful</label><br>
    <label for="curious"><input id="curious" type="checkbox" name="personality"> Curious</label><br>
  </form>
</main>
```