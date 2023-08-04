# Core OOP in JavaScript - 1st Edition

# Chapter 1: Introduction to JavaScript

JavaScript is a compiled/interpreted programming language. In other words, JavaScript is a programming language that gets compiled and interpreted, but it happens during runtime. [To read more](https://www.instagram.com/p/CvQO4BHo_dJ/?img_index=1)

## Is JavaScript Object-Oriented?

[As per Wikipedia definition, it's a high level prototyped object-oriented program](https://en.wikipedia.org/wiki/JavaScript).

[As per MDN, JavaScript is a prototype-based, multi-paradigm, single-threaded, dynamic language, supporting object-oriented, imperative, and declarative (e.g. functional programming) styles](https://developer.mozilla.org/en-US/docs/Web/JavaScript).

So in summary, from the definition of Object-Oriented Programming; yes JavaScript is object-oriented program.

## Note

Both the primitive and reference types in JavaScript are behind the hood reconstructed to an object, and that means even the primitive value is just an object, and that's why every primitive value has a constructor object attached to it(e.g: ```"Name".constructor``` will return **```String constructor```**). [More on Primitive types](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)

## Code snippet to show you that everything in JavaScript is object

```js
/***
 * The below code is to show you that everything in JavaScript is object
 * Note, if you see an anti-pattern comment on a code, it means its a bad practice
 */

/**
 * String is an object also
 */
const name = 'Emmanuel Onah';

name.random = 'Random';

console.log(name.random); // 'Random'

/***
 * arrow function is an object and we can modularize it to make its content
 * accessible as object property or method
 */
const getUser = () => {
  return {
    name: "Creative Developer",
    occupation: "JavaScript Engineer",
    mission: "To make good JavaScript practice easily accessible"
  };
};

getUser.anything = 'anything';
console.log('GBE', getUser.anything); // 'GBE' 'anything'

const user = getUser();
console.log("User name:", user.name, "\n");
console.log("User occupation:", user.occupation, "\n");
console.log("User mission:", user.mission, "\n\n");

//Anti-pattern: Array as a key-value object
const antiPatternUsers = ["Creative Adams", "Creative Jerry"];
antiPatternUsers.harry = "Creative Harrison";
console.log(antiPatternUsers);
console.log("Anti-pattern Users", antiPatternUsers.harry);

/***
 * what just happened here? harry is accessible as object property inside an array how?
 * Well,thats because behind the hood everything in JavaScript is just converted to object,
 * and object are key-value pair and what we just did is to create a key and its value.
 * 
 * Meanwhile, array are special objects with internal keys of integers known as index.
 * 
 * Please this is an anti-pattern and you will loose the feature of array iteration when
 * you do these because harry will not be iterated on!😀😀
 */

antiPatternUsers.forEach((user, i) => console.log(user, i));
```
