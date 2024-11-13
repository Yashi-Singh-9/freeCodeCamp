# Add Images to Your Website

### Description

You can add images to your website by using the `img` element, and point to a specific image's URL using the `src` attribute.

An example of this would be:

```html
<img src="https://www.freecatphotoapp.com/your-image.jpg">
``` 

Note that `img` is a void element.

All `img` elements must have an `alt` attribute. The text inside an `alt` attribute is used for screen readers to improve accessibility and is displayed if the image fails to load.

Note: If the image is purely decorative, using an empty `alt` attribute is a best practice.

Ideally the `alt` attribute should not contain special characters unless needed.

Let's add an `alt` attribute to our `img` example above:

```html
<img src="https://www.freecatphotoapp.com/your-image.jpg" alt="freeCodeCamp logo">
```

Let's try to add an image to our website:

Within the existing main element, insert an img element before the existing p elements.

Now set the `src` attribute so that it points to the url `https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg`

Finally, don't forget to give your `img` element an `alt` attribute with applicable text.

### Tests

1. Your page should have an image element.
2. Your image should have a `src` attribute that points to the kitten image.
3. Your image element's `alt` attribute should not be empty.

### Solution

```html
<h2>CatPhotoApp</h2>
<main>


  <p>Kitty ipsum dolor sit amet, shed everywhere shed everywhere stretching attack your ankles chase the red dot, hairball run catnip eat the grass sniff.</p>
  <p>Purr jump eat the grass rip the couch scratched sunbathe, shed everywhere rip the couch sleep in the sink fluffy fur catnip scratched.</p>
    <img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back.">
</main>
```