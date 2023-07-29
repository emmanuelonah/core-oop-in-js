# Core OOP in JavaScript - 1st Edition

# Chapter 1: Pillars of OOP

# Polymorphism

## What is Polymorphism?

Polymorphism is derived from the two words:
**Poly**: Many
**Morph**: Change from one form to another form.

In simple term, Polymorphism in JavaScript is the ability of a parent constructor to serve as a signatory interface of different child constructors(extender constructor). Note, this definition if deeply looked into, its restricted to SubType Polymorphism. In general term, polymorphism is the ability to change from one form to many other forms.

Meanwhile, an interface is a signatory code of how a program should be implemented and that's basically what Polymorphism does using the parent constructor as the interface.

## Types of Polymorphism

1. Ad-hoc Polymorphism
2. Parametric Polymorphism
3. SubType Polymorphism

Note: Because this course is focused on **object-oriented programming**, we will be focusing more on the **SubType polymorphism** while we just touch on the type of polymorphism.

## 1. Ad-hoc Polymorphism

This is a type of polymorphism that changes from one form to another without initial planning or coverage.

## Types of Adhoc Polymorphism

1. Function Overloading
2. Operator Overloading
3. Coercion Polymorphism

## 2. Parametric Polymorphism

From the name I believe you can detect that it's related to a parameter. So, this polymorphism accommodates any kind of data types as its parameter. e.g an object or array taken in different data-type, higher-order functions taken in an array and returns a new array.

## 3. SubType Polymorphism

This is a type of Polymorphism where a parent constructor creates a signatory interface(methods) that gets transformed by different entities(consumer constructor).

## Summary

From my scientific analysis of **SubType Polymorphism** to make it easier to understand, we can see that it's made up of the word **SubType** which simply means if there is a **SubType(SubClass/SubConstructor)** there must be a **SupType(SuperClass/SuperConstructor)** where the **SubType** is a subordinate of the **SupType**. So it's more of SuperType(Parent constructor) allowing the SubType(child constructor) to inherit and transform its content(basically methods).

## Code snippet for polymorphism in JavaScript

```js
// Note: this is focused on SubType Polymorphism

// @SuperConstructor below
function World(country) {
 if (!new.target) return new World();

 this.country = country;
}

World.prototype.getCountry = function () {
 return this.country;
};

World.prototype.alert = function () {
 return `Ohhh, ${this.country} is part of the world.`;
};

// @SubConstructor below aka SubType
function Estonia() {}

//extension aka inheritance
Estonia.prototype = new World('Estonia');

//transformation
Estonia.prototype.alert = function () {
 return `Ohhh, ${this.country} is a country in the Baltics EU.`;
};

function Nigeria() {}
//extension aka inheritance
Nigeria.prototype = new World('Nigeria');

//transformation
Nigeria.prototype.alert = function () {
 return `Ohhh, ${this.country} is a country in the ECOWAS West Africa.`;
};

//results of the different formation
const world = new World('USA');
console.log(world.alert());

const estonia = new Estonia();
console.log(estonia.alert());

const nigeria = new Nigeria();
console.log(nigeria.alert());

```
