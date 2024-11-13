# Create a Bulleted Unordered List

### Description

HTML has a special element for creating unordered lists, or bullet point style lists.

Unordered lists start with an opening `<ul>` element, followed by any number of `<li>` elements. Finally, unordered lists close with a `</ul>`.

For example:

```html
<ul>
  <li>milk</li>
  <li>cheese</li>
</ul>
```

would create a bullet point style list of `milk` and `cheese`.

Remove the last two `p` elements and create an unordered list of three things that cats love at the bottom of the page

### Tests

1. Create a `ul` element.
2. You should have three `li` elements within your `ul` element.
3. Your `ul` element should have a closing tag.
4. Your `li` elements should have closing tags.
5. Your `li` elements should not contain an empty string or only white-space.

### Solution

```html
<h2>CatPhotoApp</h2>
<main>
  <p>Click here to view more <a href="#">cat photos</a>.</p>

  <a href="#"><img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back."></a>

  <p>Kitty ipsum dolor sit amet, shed everywhere shed everywhere stretching attack your ankles chase the red dot, hairball run catnip eat the grass sniff.</p>
  <p>Purr jump eat the grass rip the couch scratched sunbathe, shed everywhere rip the couch sleep in the sink fluffy fur catnip scratched.</p>

  <ul>
    <li>catnip</li>
    <li>laser pointers</li>
    <li>lasagna</li>
  </ul>
</main>
```