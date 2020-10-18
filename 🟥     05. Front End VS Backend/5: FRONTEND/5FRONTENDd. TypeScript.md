## TypeScript

Make sure you read the article on JavaScript first, otherwise this won't make any sense!

### Why TypeScript

You're probably impressed with the flexibility that JavaScript, a dynamically-typed language, offers a programmer. There are relatively few keywords in the language, all variables can be assigned any type, and the syntax is reminiscent of Java without a lot of the rules. All objects are inherently ill-defined, with the flexibility to assign any object any property as you see fit. 

Sounds wonderful right? Well in some cases yes, some cases no. For smaller projects, this flexibility works fine (great even), but for larger, more complicated projects with more developers, this flexibility turns into a nightmare very quickly. Other dynamically-typed languages like Python have ways to enforce typing natively, but JavaScript does not currently. Given how popular JavaScript was becoming and how much interactive web-pages were forcing on JS developers, a change needed to happen. 

That change was [TypeScript](https://www.typescriptlang.org/), created by Microsoft in 2012. The language is still being updated pretty regularly, and is open-source.

### What is TypeScript?

TypeScript is a superset of JavaScript which is used to enforce static typing on the language, as well as some additional syntax rules for added sanity (such as easy to use packaging and scoping). All TypeScript can become valid JavaScript, but not all JavaScript can become valid TypeScript. A TypeScript interpreter is used to convert ([transpile](https://stackoverflow.com/questions/44931479/compiling-vs-transpiling)) TypeScript code (`*.ts`) files into JavaScript files (`*.js`). The TypeScript interpretter checks at "compile" time for logical errors similar to a language like Java or C++ to minimize the amount of runtime errors that occur, and will prevent compilation until the errors are fixed.

TypeScript is designed to make use of the latest and greatest JavaScript updates that may not be on all browsers (such as `await`/`async`, `const`, `let`, arrow functions, etc.), while JavaScript is much more environment-dependent upon all of the features it has (Internet Explorer for example). TypeScript is able to bring newer features into older constructs easier than just JavaScript alone.

For this reason, TypeScript is often the preferred for new projects that will be sufficiently large, and is used in many front-end development frameworks (TypeScript is used in Angular, optional in Vue, and inspired some elements in React). NodeJS is also compatible with TypeScript.

### TypeScript vs JavaScript in Action
The file `fib.ts` became `fib.js` after running the `tsc` (TypeScript Compile) command.
#### `fib.ts`
```
function fibonacci (num: number): number {
  if (num == 0) { 
    return 0;
  }
  if (num == 1) {
    return 1;
  }
  const sum = fibonacci(num - 1) + fibonacci(num - 2);
  return sum;
}

console.log(fibonacci(5));
# console.log(fibonacci('5')); would cause an error and prevent compilation
```
#### `fib.js`
```
function fibonacci(num) {
    if (num == 0) {
        return 0;
    }
    if (num == 1) {
        return 1;
    }
    var sum = fibonacci(num - 1) + fibonacci(num - 2);
    return sum;
}
console.log(fibonacci(5));
# console.log(fibonacci('5')); Would run just fine by performing type coercion.
```

Note that for more complex functions, the transpiled JavaScript will likely look much different from the original TypeScript. TypeScript will also prevent errors like missing return statements and other compiler errors seen in other languages.

### Further Reading
- [TypeScript Docs](https://en.wikipedia.org/wiki/TypeScript)
- [TypeScript Source Code](https://github.com/microsoft/TypeScript)
- [TypeScript - The Basics](https://www.youtube.com/watch?v=ahCwqrYpIuM)
