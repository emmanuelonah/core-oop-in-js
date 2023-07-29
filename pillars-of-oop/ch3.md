# Core OOP in JavaScript - 1st Edition

# Chapter 3: Pillars of OOP

# Inheritance

## Table of content

1. Inheritance by prototype
2. Inheritance by mixins

## What is Inheritance by prototype?

A prototype is an object of a constructor that can be used to enhance a constructor(add properties/methods) or used to extend another constructor content(properties/methods).
Note, by default the prototype object is present on every constructor(function invoked with the new keyword). But can be set on an object literal using Object.setPrototypeOf(obj,prototype).

[To read more on the prototype](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes)&nbsp;
[To read more on setting prototype on object literal](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/setPrototypeOf)&nbsp;

## How to inherit from another constructor?

First and famous, in inheritance, we have what we call the **superclass** and the **subclass**.

1. **A superclass**: is a class(constructor) that gets inherited by another class(the consumer or child constructor). We can call it the parent constructor.
2. **A subclass**: is a class(constructor) that inherits from the owner class(constructor). We can call it the child constructor.

### We inherit using this syntax

```js
ChildConstructor.prototype = Object.create(ParentConstructor.prototype);
```

### Above code explanation

- We are assigning the right-hand side (the superclass) as a value to the prototype object of the left-hand side(the subclass).
- Object.create: is a way of creating a **"sequelized object"**, that when mutated it won't affect the initial reference(Because in object what we do is referencing). So with Object.create, we take the existing object(content inside the Object.create) to be the prototype of the newly created object(left-hand side).
- [To read more on Object.create](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)

### Code snippet for prototype inheritance

```js
//Super constructor aka parent constructor
function Person() {
 if (!new.target) return arguments.callee();
}

Person.prototype.greet = function () {
 return 'Good day!';
};
const lady = new Person();

//Sub constructor aka child constructor
function Lady() {
 if (!new.target) return arguments.callee();
}
Lady.prototype = Object.create(Person.prototype);

const sasha = new Lady();
console.log(sasha.greet());
```

------

## What is Inheritance by mixins?

According to Wikipedia, a mixin is a class containing methods that can be used by other classes without a need to inherit from it. Basically, a mixin is an object containing methods that get transferred to different constructors without inheritance practice.

## Why mixin?

- In JavaScript, a constructor can only inherit one constructor at a time.
- So, mixin helps us copy methods or properties into our own constructor(and that's where the word **mixin** came from because we are **mixing** external properties/methods with our internal constructor properties/methods).
- It helps to avoid duplication of code.

## How to create mixin

```js
Object.assign(MyConstructor.prototype, mixinObject);
```

[To read more about mixin](<https://javascript.info/mixins>)
[To read about Object.assign](<https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign>)
**Note**: While reading Object.assign, pay attention to enumerable and non-enumerable object(iterable object and vice-versa using for in).

### Code snippet for mixin inheritance

```js
//Super constructor aka parent constructor
function Person() {
 if (!new.target) return Person();
}
Person.prototype.greet = function () {
 return 'Good day!';
};

//Sub constructor aka child constructor
function Lady() {
 if (!new.target) return Lady();
}
Lady.prototype = Object.create(Person.prototype);

// Mixins
const greetings = {
 greetInEstonia: () => 'Tere!',
 greetInRussia: () => 'Previet',
 greetInIgbo: () => 'Ndewo',
 greetInHausa: () => 'Sanu',
 greetInYoruba: () => 'Okaro',
};

//Below we copying greetings mixins to Lady prototype
Object.assign(Lady.prototype, greetings);

const sasha = new Lady();
console.log(sasha.greet());
console.log(sasha.greetInEstonia());
console.log(sasha.greetInRussia());
console.log(sasha.greetInIgbo());
console.log(sasha.greetInHausa());
console.log(sasha.greetInYoruba());

```
