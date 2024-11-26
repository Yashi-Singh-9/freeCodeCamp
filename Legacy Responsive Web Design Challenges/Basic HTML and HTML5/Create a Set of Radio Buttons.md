# Create a Set of Radio Buttons

### Description

You can use *radio buttons* for questions where you want the user to only give you one answer out of multiple options.

Radio buttons are a type of `input`.

Each of your radio buttons can be nested within its own `label` element. By wrapping an `input` element inside of a `label` element it will automatically associate the radio button input with the label element surrounding it.

All related radio buttons should have the same `name` attribute to create a radio button group. By creating a radio group, selecting any single radio button will automatically deselect the other buttons within the same group ensuring only one answer is provided by the user.

Here's an example of a radio button:

```html
<label> 
  <input type="radio" name="indoor-outdoor">Indoor 
</label>
```

It is considered best practice to set a `for` attribute on the `label` element, with a value that matches the value of the `id` attribute of the `input` element. This allows assistive technologies to create a linked relationship between the label and the related `input` element. For example:

```html
<input id="indoor" type="radio" name="indoor-outdoor">
<label for="indoor">Indoor</label>
```

We can also nest the `input` element within the `label` tags:

```html
<label for="indoor"> 
  <input id="indoor" type="radio" name="indoor-outdoor">Indoor 
</label>
```

---

Add a pair of radio buttons to your form, each nested in its own `label` element. One should have the option of `indoor` and the other should have the option of `outdoor`. Both should share the `name` attribute of `indoor-outdoor` to create a radio group.

### Tests

1. Your page should have two `radio` button elements.
2. Your radio buttons should be given the `name` attribute of `indoor-outdoor`.
3. Each of your two radio button elements should be nested in its own `label` element.
4. Each of your `label` elements should have a closing tag.
5. One of your radio buttons should have the label `indoor`.
6. One of your radio buttons should have the label `outdoor`.
7. Each of your radio button elements should be added within the `form` tag.

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
    <!-- Text input for cat photo URL -->
    <input type="text" placeholder="cat photo URL" required>
    
    <!-- Radio buttons for indoor or outdoor option -->
    <label for="indoor">
      <input id="indoor" type="radio" name="indoor-outdoor">Indoor
    </label>
    <label for="outdoor">
      <input id="outdoor" type="radio" name="indoor-outdoor">Outdoor
    </label>

    <!-- Submit button -->
    <button type="submit">Submit</button>
  </form>
</main>
```