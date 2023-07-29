# Core OOP in JavaScript - 1st Edition

# Chapter 1: Instantiation(new keyword) in JavaScript

## What is instantiation in OOP?

[According to the Cambridge dictionary, the English meaning of Instantiation is "something that represents or is an example of something else](https://dictionary.cambridge.org/dictionary/english/instantiation).

Our definition: Instantiation in OOP is a process of creating an object from a given structure/blueprint(constructor).

## Creating an instance of a constructor

**We use the ```new``` keyword to create an instance**

```js
new World();
```

**What does the ```new``` keyword do?**

- Tells Js engine that the function is not a regular function but
  a constructor therefore create a blank object called the ```this``` object.
- Injects the constructor prototype into the ```this``` object to make the
  prototype fields accessible by the constructor instance.
- Returns ```this``` object if the constructor doesn't return an explicit object.

[For more on constructor in js](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new)

## Code snippet on JavaScript instantiation

```js

function Country(name) {
  this.name = name;
  this.defaultGreeting = "Hello!"

  this.greet = function () {
    if (this.name === "Estonia") return "Tere!";
    
    return this.defaultGreeting;
  };
}


const estonia = new Country("Estonia");
console.log("Estonia says", estonia.greet());

const germany = new Country("Germany");
console.log("Germany says", germany.greet());
```
