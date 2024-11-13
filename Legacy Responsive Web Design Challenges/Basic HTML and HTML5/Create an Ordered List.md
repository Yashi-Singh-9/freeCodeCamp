# Create an Ordered List

### Description

HTML has another special element for creating ordered lists, or numbered lists.

Ordered lists start with an opening `<ol>` element, followed by any number of `<li>` elements. Finally, ordered lists are closed with the `</ol>` tag.

For example:
```html
<ol>
  <li>Garfield</li>
  <li>Sylvester</li>
</ol>
```

would create a numbered list of `Garfield` and `Sylvester`.

---

Create an ordered list of the top 3 things cats hate the most.

### Tests

1. You should have an ordered list for `Top 3 things cats hate`:
2. You should have an unordered list for `Things cats love`:
3. You should have only one `ul` element.
4. You should have only one `ol` element.
5. You should have three `li` elements within your `ul` element.
6. You should have three `li` elements within your `ol` element.
7. Your `ul` element should have a closing tag.
8. Your `ol` element should have a closing tag.
9. Your `li` element should have a closing tag.
10. The `li` elements in your unordered list should not be empty.
11. The `li` elements in your ordered list should not be empty.

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
</main>
```