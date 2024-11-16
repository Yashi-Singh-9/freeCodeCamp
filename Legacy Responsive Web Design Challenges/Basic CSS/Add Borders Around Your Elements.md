# Add Borders Around Your Elements

### Description

CSS borders have properties like `style`, `color` and `width`.

For example, if we wanted to create a red, 5 pixel border around an HTML element, we could use this class:

```css
<style>
  .thin-red-border {
    border-color: red;
    border-width: 5px;
    border-style: solid;
  }
</style>
```

---

Create a class called `thick-green-border`. This class should add a 10px, solid, green border around an HTML element. Apply the class to your cat photo.

Remember that you can apply multiple classes to an element using its `class` attribute, by separating each class name with a space. For example:

```html
<img class="class1 class2">
```

### Tests

1. Your `img` element should have the class `smaller-image`.
2. Your `img` element should have the class `thick-green-border`.
3. Your image should have a border width of `10px`.
4. Your image should have a border style of `solid`.
5. The border around your `img` element should be green.

### Solution

```html
<link href="https://fonts.googleapis.com/css?family=Lobster" rel="stylesheet" type="text/css">
<style>
  .red-text {
    color: red;
  }

  h2 {
    font-family: Lobster, monospace;
  }

  p {
    font-size: 16px;
    font-family: monospace;
  }

  .smaller-image {
    width: 100px;
  }

  .thick-green-border{
    border-style: solid;
    border-color: green;
    border-width: 10px;
  }
</style>

<h2 class="red-text">CatPhotoApp</h2>
<main>
  <p class="red-text">Click here to view more <a href="#">cat photos</a>.</p>

  <a href="#"><img class="smaller-image thick-green-border" src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back."></a>

  <div>
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
  </div>

  <form action="https://freecatphotoapp.com/submit-cat-photo">
    <label><input type="radio" name="indoor-outdoor" checked> Indoor</label>
    <label><input type="radio" name="indoor-outdoor"> Outdoor</label><br>
    <label><input type="checkbox" name="personality" checked> Loving</label>
    <label><input type="checkbox" name="personality"> Lazy</label>
    <label><input type="checkbox" name="personality"> Energetic</label><br>
    <input type="text" placeholder="cat photo URL" required>
    <button type="submit">Submit</button>
  </form>
</main>
```