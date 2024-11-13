# Nest an Anchor Element within a Paragraph

### Description

You can nest links within other text elements.

```html
<p>
  Here's a <a target="_blank" href="https://www.freecodecamp.org"> link to www.freecodecamp.org</a> for you to follow.
</p>
```

Let's break down the example. Normal text is wrapped in the `p` element:

```html
<p> Here's a ... for you to follow. </p>
```

Next is the *anchor* element `<a>` (which requires a closing tag `</a>`):

```html
<a> ... </a>
```

`target` is an anchor tag attribute that specifies where to open the link. The value `_blank` specifies to open the link in a new tab. The `href` is an anchor tag attribute that contains the URL address of the link:

```html
<a href="https://www.freecodecamp.org" target="_blank"> ... </a>
```

The text, `link to www.freecodecamp.org`, within the `a` element is called anchor text, and will display the link to click:

```html
<a href=" ... " target="...">link to freecodecamp.org</a>
```

The final output of the example will look like this:

Here's a [link to www.freecodecamp.org](https://www.freecodecamp.org/) for you to follow.

---

Nest the existing `a` element within a new `p` element. Do not create a new anchor tag. The new paragraph should have text that says `View more cat photos`, where `cat photos` is a link, and the rest is plain text.

### Tests

1. You should only have one `a` element.
2. The `a` element should link to "`https://www.freecatphotoapp.com`".
3. Your `a` element should have the anchor text of `cat photos`
4. You should create a new `p` element. There should be at least 3 total `p` tags in your HTML code.
5. Your `a` element should be nested within your new `p` element.
6. Your `p` element should have the text `View more ` (with a space after it).
7. Your `a` element should not have the text `View more`.
8. Each of your `p` elements should have a closing tag.
9. Each of your `a` elements should have a closing tag.

### Solution

```html
<h2>CatPhotoApp</h2>
<main>

  <p>View more <a href="https://www.freecatphotoapp.com" target="_blank">cat photos</a></p>

  <img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back.">

  <p>Kitty ipsum dolor sit amet, shed everywhere shed everywhere stretching attack your ankles chase the red dot, hairball run catnip eat the grass sniff.</p>
  <p>Purr jump eat the grass rip the couch scratched sunbathe, shed everywhere rip the couch sleep in the sink fluffy fur catnip scratched.</p>
</main>
```