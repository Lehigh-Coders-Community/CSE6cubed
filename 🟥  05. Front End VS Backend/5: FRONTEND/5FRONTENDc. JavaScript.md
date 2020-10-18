## JavaScript

Some important things to keep in mind.

- The name is frustratingly close to Java. It is not Java. If you know Java, you might recognize some of the syntax. But, I want to be clear that your resume will be shreaded if you list Java/JavaScript in your skills section.
- The core of the JavaScript programming language was made in [10 days](https://www.checkmarx.com/blog/javascript-history-infographic/). This gives it some ... [quirks](https://www.destroyallsoftware.com/talks/wat) (skip to 1:20).
- When watching the video about JavaScript's quirks, you'll notice that it isn't throwing an error...it just keeps going like [The Black Night](https://www.youtube.com/watch?v=ZmInkxbvlCs) in Monty Python. No error can stop it from continuing to run. Why would we want that? In the context of the web, this can make some sense. We don't want the entire website to stop working because of some error. This does, however, make web development debugging frustrating.
- If you aren't convinced - Microsoft wasn't either. They wrote TypeScript - which has types and a bunch of other helpful features & gets compiled into JavaScript.

### Basics

Let's get some basics out of the way so that way we can focus on the following question: How would making this more dynamic make this more helpful?

JavaScript is a fully-fledged programming language. It, like CSS, has its own tag `<script>`, and code in that tag uses a different syntax. Let's run through it.

```javascript
// This is a comment

// this is a variable
var a = 0;

// this is a function
function myFunction() {
  var funcVariable = "Old Value";
  return "Other Value";
}

// this is how you call a function - any code beyond here can access the funcVariable
myFunction();
funcVariable = "New Value";

// JavaScript lets you concat strings like this, it'll even automatically convert numbers to strings
funcVariable = funcVariable + ", Newer Value" + 2;

// JavaScript has objects
var obj = { field1: a, field2: funcVariable };

// JavaScript has arrays
var array = [obj, obj, obj];

// It has IF STATEMENTS
if (array.length > 1) {
  // You can add contents to an array like this, and have different types in the same array
  array.push(myFunction());
}

// This is a for loop - note var i = 0 (NOT INT)
for (var i = 0; i < array.length; i++) {
  //
}

// This is a while loop - (won't run because of previous i value)
while (i < array.length) {
  //
}
```

The output of this nonsense is: [{"field1":0,"field2":"New Value, Newer Value2"},{"field1":0,"field2":"New Value, Newer Value2"},{"field1":0,"field2":"New Value, Newer Value2"},"Other Value"]

### Modifying The HTML

JavaScript gives us an object called "document", you can do a bunch of [fancy things](https://www.w3schools.com/jsref/dom_obj_document.asp) with it, but most of the time you want to change the value of something in the HTML to equal some value you generated in JavaScript. So let's do that.

We take the document object, and use a function called "getElementByID()". We then refrence the innerHTML property (this replaces what you put inside `<p></p>`)

```javascript
document.getElementById("demo").innerHTML = "New Value!";
```

### JSON

That's cool, but we don't have a string like shown in the example above. We have an object. There is a lot of times when we need to convert objects --> strings or strings --> objects. This especially comes up when sending data to/from a server.

So, in order to convert that "array" object from above to a string, we use JSON - specifically JSON.stringify() (if we wanted to turn a string into an object, we'd use [JSON.parse()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse))

```javascript
document.getElementById("demo").innerHTML = JSON.stringify(array);
```

Now that that's all done - we can finally look at the [code](https://www.w3schools.com/code/tryit.asp?filename=GJ63B276HYJ4)!
Don't forget to hit "RUN".

### Events

Okay, that's cool and all, but this JavaScript runs when the page is loaded, which doesn't always make sense. Sometimes we want interactivity when a user clicks something. For that, we have events. The most common of these is onclick. [Click here to learn more.](https://www.w3schools.com/js/js_events.asp)

### Wrap Up

My goal here wasn't to teach you JavaScript, just to teach you enough to understand (1) how it is different from other languages you have learned and (2) how it makes pages more interactive - you saw how we were able to calculate a value and present it to the user.

Some things to look into if you are interested in learning more:

- [Cookies](https://www.w3schools.com/js/js_cookies.asp)
- [Regular Expressions](https://www.w3schools.com/js/js_regexp.asp)
- [Error Handling](https://www.w3schools.com/js/js_errors.asp)
- [ES6](https://www.w3schools.com/js/js_es6.asp)

[W3Schools JavaScript Docs](https://www.w3schools.com/js/default.asp)
