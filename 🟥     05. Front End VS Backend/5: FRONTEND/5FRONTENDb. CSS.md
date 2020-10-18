## CSS

This isn't going to be a replacement for

- Looking up CSS properties (I still need to)
- Trying random things and seeing what works (I still do)

---

Honestly, there isn't a really helpful answer to "How should we make this look?". The answer has changed a lot, websites used to look pretty different back in _checks notes_ 2019 for E-ZPass.
![E-ZPass Website](https://external-preview.redd.it/Pz0R1VRu0OphsaNCW3tNLOh0ZcXK5pLTZz8fncI1UtE.jpg?auto=webp&s=9712039edb4aebede4ca07985950dfc38b5b160a)

### How do other people think my website should look?

Different people have different thoughts about how websites should look - at this point, [Google](https://material.io/design) has the most comprehensive opinions on the matter.

### How do I make things look the way I want in CSS?

This starts by targeting the right part of the HTML to style:

We can target certain tags:

```CSS
body {
    /* Set the background color of <body> to #fff */
    background-color: #fff;
}
```

We can target certain individual items on a page by their ID:

```CSS
#id1 {
    /* Set the font size of <p id="id1"></p> to 16px */
    font-size: 16px;
}
```

We can target a certain group of items on a page by their CLASS:

```CSS
.class-one {
    /* Set the spacing around the text of <p class="class-one"></p> to 12px */
    padding: 12px;
}
```

Here are some things to do your own research into:

- [Margin VS Padding](https://stackoverflow.com/questions/2189452/when-to-use-margin-vs-padding-in-css)
- [Flexbox](https://joeattardi.codes/introduction-to-flexbox)

### Where can I learn more?

The two places where I learned how to style, and what my own style for web-dev was involved in two websites:

- [W3Schools](https://www.w3schools.com/css/default.asp) teaches the CSS fundamentals very well.
- [CodePen](https://codepen.io/) is an excellent website for seeing what others are writing.
