# Core OOP in JavaScript - 1st Edition

# Chapter 1: Function Bindings

## Why teaching Bind as a bonus course?

My aim for teaching **bind** is to help you understand the power of **function** and **this** keyword.

## For React Engineers

If you are experienced with React, you should have written a code in the early days of **React** where you have to bind every method of the class in other to make it accessible via the **this** object or better still you make use of "arrow function" for creating methods. The reason why you can escape the undefined error when using the "arrow function" is because any function created with an arrow syntax automatically gets scoped by the parent and becomes the "variable" of the parent scope(either the class or window object), this enable the arrow function to have access to the parent this object. But when you use function literals, the ```this``` keyword reference to the function itself and ends up not finding things like "this.setState" as the content of the function.

## What is Binding?

From google search, Binding means to stick together or cause to stick together in a single mass.

In JavaScript, binding methods or binding is a special technique of a function that allows the injection of an object(key-value pair) that the functions ```this``` object will refer to.

## Types of Binding in JavaScript

1. bind()
2. call()
3. apply()

## 1. bind()

**The bind() method**: creates a new function that, when called, has its this keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.
[Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind)

## 2. call()

**The call() method**: calls a function with a given this value and arguments provided individually.
[Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call)

## 3. apply()

**The apply() method**: calls a function with a given this value, and arguments provided as an array (or an array-like object).
[Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)

## Code snippet of ```bind()```

```js
const user = {
  name: "Omo Yoma",
  occupation: "Makeup artist"
};

function getUser() {
  return `${this.name} is a very hardworking ${this.occupation}`;
}

//bind always creates a new function
const boundGetUser = getUser.bind(user);
console.log(boundGetUser());

```

## Code snippet of ```call()```

```js
const user = {
  name: "Sasha Blanca",
  occupation: "Computer scientist"
};

function getUser() {
  return `${this.name} is a very smart ${this.occupation}`;
}

console.log(getUser.call(user));
```

## Code snippet of ```apply()```

```js
const user = {
  name: "Emmanuel Onah",
  occupation: "Software engineer"
};

function getUser(city) {
  return `${this.name} is a very stubborn ${this.occupation} from ${city}`;
}

console.log(getUser.apply(user, ["Nigeria"]));
```
