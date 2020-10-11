## TypeScript

Make sure you read the article on JavaScript first, otherwise this won't make any sense!

### Why TypeScript

You're probably impressed with the flexibility that JavaScript, a dynamically-typed language, offers a programmer. There are relatively few keywords in the language, all variables can be assigned any type, and the syntax is reminiscent of Java without a lot of the rules. All objects are inherently ill-defined, with the flexibility to assign any object any property as you see fit. 

Sounds wonderful right? Well in some cases yes, some cases no. For smaller projects, this flexibility works fine (great even), but for larger, more complicated projects with more developers, this flexibility turns into a nightmare very quickly. Other dynamically-typed languages like Python have ways to enforce typing natively, but JavaScript does not currently. Given how popular JavaScript was becoming and how much interactive web-pages were forcing on JS developers, a change needed to happen. 

That change was [TypeScript](https://www.typescriptlang.org/), created by Microsoft in 2012. The language is still being updated pretty regularly, and is open-source.

### What is TypeScript?

TypeScript is a subset of JavaScript which is used to enforce static typing on the language, as well as some additional syntax rules for added sanity. All TypeScript can become valid JavaScript, but not all JavaScript can become valid TypeScript. A TypeScript interpreter is used to convert ([transpile](https://stackoverflow.com/questions/44931479/compiling-vs-transpiling)) TypeScript code (`*.ts`) files into JavaScript files (`*.js`). TypeScript is design to make use of the latest and greatest JavaScript updates that may not be on all browsers (such as `await`/`async`, `const`, `let`, arrow functions, etc.), while JavaScript is much more environment-dependent upon all of the features it has. TypeScript is able to bring newer features into older constructs easier than just JavaScript alone.

### TypeScript vs JavaScript in Action
