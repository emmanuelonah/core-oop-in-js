# Core OOP in JavaScript - 1st Edition

# Chapter 2: Pillars of OOP

# Encapsulation

## Table of content

1. What is private in OOP?
2. What is public in OOP?
3. What is static?

## What is private in OOP?

**private property/method**: are those contents of the constructor that "can never" be accessible outside the constructor scope. i.e it's an internal variable and when you instantiate or extend the constructor you can't access it.

## Code snippet of private property/method

```js
function Occupation() {
  // this is a public variable
  this.exclaimed = "";

  // this is private variable
  const occupationSynonyms = "Job";

  // this is private method
  const setExclaim = () => {
    this.exclaimed = `Yeah, i love my ${occupationSynonyms}.`;
  };
  setExclaim();
}

const occupation = new Occupation();
console.log(occupation.exclaimed); // "Yeah, i love my job"

console.log(occupation.occupationSynonyms); //undefine
console.log(occupation.setExclaim); //undefine
```

------

## What is public in OOP?

**public property/method**: are those contents of the constructor that "can be" accessed outside the constructor scope. i.e it's even accessible to the instance of the constructor.

## Code snippet of public property/method

```js
function Occupation() {
  //this is a public variable
  this.occupationSynonyms = "Job";

  //this is a public method
  this.exclaim = function () {
    return `Yeah, i love my ${this.occupationSynonyms}.`;
  };
}

const occupation = new Occupation();
console.log(occupation.occupationSynonyms); //job
console.log(occupation.exclaim()); // "Yeah, i love my job"
```

------

## What is static?

**static property/method**: are those property or method that can be accessed through the constructor itself and not through the instance.

## Why should you use a static property/method?

- If you want a value/result to remain the same across instantiation.
- If a property or method has nothing in relation to an instance of a constructor, then make it static e.g use static method for init-time-branching or standalone configuration.

## Code snippet of static property/method

```js
function Occupation() {
  //this is a public variable
  this.occupationSynonyms = "Job";

  //this is a public method
  this.exclaim = function () {
    return `Yeah, i love my ${this.occupationSynonyms}, because ${Occupation.reason}`;
  };

  //this is a public method
  this.inform = function () {
    return Occupation.alert();
  };
}

// this is a static variable
Occupation.reason = "its my purpose?";

//this is a static method
Occupation.alert = function () {
  return "If you don't love what you do then make a change because life is short";
};

const occupation = new Occupation();
console.log(occupation.exclaim());
console.log(occupation.inform());
```
