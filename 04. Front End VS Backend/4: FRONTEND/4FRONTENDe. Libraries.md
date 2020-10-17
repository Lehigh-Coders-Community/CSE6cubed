## Frontend Libraries
---
Welcome to the next stage of the frontend gauntlet - libraries. Fear not, though, these will make your day when you compare them to the raw, bare-bone nature of the Big Three (JS, HTML, & CSS).

### They're Different Than Frameworks

Frontend libraries are meant to streamline the process of implementing a wide variety of code. On the frontend, there is code to be written for virtually anything you can think of on the envisioned webpage, ranging from the state of a value to the type of rendering which occurs as you travel to a URL.

*Libraries* will be run in your code, versus *frameworks* which run your code.

Mostly, libraries and frameworks deal with the JS of your frontend trifecta. Having your JavaScript compartmentalized is quite helpful, especially when you're looking for efficiency in your own development experience. However, mastering libraries and frameworks is an entire challenge in itself.

### Conceptually...
Libraries just pull together a lot of different code which can serve a purpose in achieving some programmatic objective. For instance, if you want to build a site, you might want to use Vue in order to handle the more complex aspects of frontend development, the "under the hood" stuff. 

---

### JavaScript Libraries

> Generally speaking, JavaScript libraries are collections of prewritten code snipppets that can be used and reused to perform common JavaScript functions. 

Library snippets can be pasted throughout the rest of a project as needed. An example you've probably heard of is [jQuery](https://jquery.com/). 

> jQuery is a fast, small, and feature-rich JavaScript library. It makes thing like HTML documental traversal and manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers. With a combination of versatility and extensibility, jQuery has changed the way that millions of people write JavaScript.

#### Example Code  
`$( "button.continue" ).html( "Next Step..." )`

Notice, jQuery utilizes the '$' character. This is a universal predicator for all jQuery usage. It is the root reference you must call whenever utilizing the library, and this is an inherent property of the library - it's just JavaScript layered ontop of more JavaScript!

Here's an example of an Ajax server call being made with jQuery.  
`$.ajax({
  url: "/api/getWeather",
  data: {
    zipcode: 97201
  },
  success: function( result ) {
    $( "#weather-temp" ).html( "<strong>" + result + "</strong> degrees" );
  }
});`

Starting to get the point?

You'll find an assortment of libraries useful throughout the lifetime of your professional career. Libraries are like packages in any other langauge. In the context of a frontend, they typically handle the procedural aspects of developing a working site. 

#### A List of Useful JavaScript Libraries
1. [React.js](reactjs.org)
- The best contemporary library for general frontend development. Countless developers have adopted this as their go-to whenever they want to whip up a project. React is easy to understand and use the JS library to build user interfaces for web applications (front-view or model of MVC architecture). React is maintained by Facebook and a few other companies. React is declarative, efficient, and flexible enough to let developers build more complex UIs using the existing pieces of code, also known as components. React is fast and scalable, hence any changes to applications do not need a page to reload. 
2. jQuery
- Query dramatically simplifies JS programming and is easy to learn and use. It is highly extensible and makes web pages load faster. jQuery wraps up a lot of standard functions making the job of the developer easy. A JS code of several lines could be just a method to be called in jQuery. It also has many plugins to perform different tasks. Some of the features of jQuery are CSS manipulation, HTML/DOM manipulation, HTML events, animations and effects, utilities, and AJAX. The best part of jQuery is the way it handles browser compatibility issues without the developer worrying about it. Some of the major IT companies like Microsoft, Netflix, and Google use jQuery. It is effortless to include jQuery in web pages.
3. [Google Polymer](https://www.polymer-project.org/)
- Created by Google, Polymer is a JS library that allows developers to reuse HTML elements and create custom elements using HTML, CSS, and JS to create more interactive applications. It is compatible with different platforms. Once you install Polymer using the command line interface or the Bower method, you can reuse already developed elements without worrying about how those were created. You can also build your custom elements using polyfills i.e., web component specifications. The custom elements can be distributed across the network and used simply by importing the required HTML. To install and use Polymer, you should be familiar with node.js, npm, Bower, Git, and Polymer CLI.
4. [DOJO](https://dojotoolkit.org/)
- The Dojo is an open-source JavaScript library that helps develop cross-platform, JS, and Ajax-based web sites in a faster manner. DOJO has a vast set of APIs and modules. 
5. [Vue.js](https://vuejs.org/)
- An alternative to React, Vue compartmentalizes many of the complex aspects of React. Vue js is based on the Virtual DOM model, much like React, and has a component-based architecture. Using templates of Vue.js, apps can be created faster. Vue also requires fewer lines of code for the same task that would need more code with other libraries. If you need a small application to be built in less time, Vue should be your perfect choice. By combining Vue with other tools and utilities, you can get a full-fledged framework. As a framework, Vue can handle complex functionalities like routing, build tooling, and state management. 
6. [JsPHP](https://www.php.net/)
- As the name suggests, JsPHP is a JS library for PHP API to be available in the JS environment. It is open-source and provides a compelling interface for JS developers who work in PHP. JsPHP can work in tandem with other libraries in an application. JsPHP supports PHP functions, including regular expressions, date-time evaluations, JSON, error handling, object manipulations, strings, XML, URL, and so 

*resources:*
https://hackr.io/blog/top-javascript-libraries
