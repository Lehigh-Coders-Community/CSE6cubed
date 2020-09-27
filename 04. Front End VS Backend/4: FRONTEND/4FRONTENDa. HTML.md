## HTML

You are going to have to look this up again after this course is over, and that's ok! I had to look this up to double check that I got everything right.

Just keep in mind this question: how do we strucutre this front end in a way that people will find intuitive? In this case, on our website.

Let's break this down into some smaller questions.

- What belongs on the same page? Should we have multiple pages?
- How do we make a page?
- What is the most important thing on this page?
- What would be the best method to show users this information?

### What belongs on the same page? Should we have multiple pages?

You've been on a website before. What kinds of information belong together? Similar information. A website should help a user find the information they need in as little time as possible.

In practice, this results in general purpose home pages that quickly narrow down to specific pages, often with custom information. Take Google. The home page is a generic page that is (roughly) what everyone seese when logging on. Then clicking on your gmail results on a highly customized page.

So, when designing your own website, every site will have a homepage - which in HTML we call an index.html file. Some users might want to learn more about our site, we can gather that information and put it in our about.html page, and some users want to manage their profile, we can display that on our profile.html page.

### How do we make a page?

HTML is quite an old language - so you have to like...tell it you want to use HTML. This uses the HTML tag. We then have some code that we might some code that we don't want users to see. This belongs in the HEADER tag. The actual contents of the page belong in the BODY tag. One final note, most websites have a different-styled bottom of the page, with legal info, links, contact info, etc. - so there is a tag for that too - FOOTER.

Code-Lab 1: Go [here](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_default) and replace the text "Page Title" with something else. Did you notice any change? (You shouldn't! That is code we don't show to the user). Now replace the text "This is a Heading" with something else. Did you notice any change? (You should. The body is what we show to the user). Don't forget to hit the big green "RUN" button to see your changes!

Code-Lab 2: Go [here](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_default) and add the footer. Where should it go? HINT: We want the user to see it. See the answer in the answers folder.

### What is the most important thing on this page?

We use headers to show what's important and to break up a long page of text (just as we do on this page, look at the size of HTML vs the header above). HTML supports this out of the book with the header tags.

```html
<h1>This is the most important</h1>
<h2>This is the second most important</h2>
<h3>This is the third most important</h3>
<!-- No one uses the rest of these (this is how you leave a comment btw!) -->
<h4>This is the fourth most important</h4>
<h5>This is the fifth most important</h5>
<h6>This is the sixth most important</h6>
```

As you can see from the comment I left, no one uses h4-h6, because we can control the size of the text using CSS (the next article).

Code-Lab 3: Go [here](https://www.w3schools.com/code/tryit.asp?filename=GJ5YLXDGWH1F) and play around with the different headers.

### What would be the best method to show users this information?

Most often, you want to show text on your website. For this we have the P tag. In this case "P" means paragraph.

```html
<p>This is some text</p>
```

Sometimes, you want to link to another part of your website / or someone else's website. We use the A tag for this. "A" stands anchor.

```html
<a href="/about">Link to your own about page</a>
<a href="https://www.nasa.gov/">Link to nasa.gov</a>
```

Sometimes, you want to have a list of content we use OL for ordered (as in numbered) list and UL for unordered (not-numbered) list. In both LI is a list item.

```html
<ol>
  <li>Ordered list item 1</li>
  <li>Ordered list item 2</li>
  <li>Ordered list item 3</li>
</ol>

<ul>
  <li>Un-ordered list item 1</li>
  <li>Un-orderedlist item 2</li>
  <li>Un-ordered list item 3</li>
</ul>
```

Sometimes, you want an image. For that we use an IMG tag. Images can be JPG, PNG or SVG - just paste the path of the image in SRC. Video and audio work basically the same way.

If you are wondering "wait why isn't it two tags like everything else?", like most things in HTML [this is for backwards compatability reasons](https://stackoverflow.com/questions/23890716/why-is-the-img-tag-not-closed-in-html). It's why websites from the 80s still pretty much work today.

```html
<img src="https://i.ibb.co/bmZgtjX/cse006cubed.png" />
```

Click [here](https://www.w3schools.com/code/tryit.asp?filename=GJ5ZG6CKPCLN) to see all of these code blocks together. It doesn't look great or do much - but that is what we are solving in the text two articles.

### Wrap Up

Great, this wraps up your introduction into HTML - if you want a comprehensive list, [W3Schools](https://www.w3schools.com/TAGs/) has a great one.
