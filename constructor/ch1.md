# Core OOP in JavaScript - 1st Edition

# Chapter 1: Constructor in JavaScript

## What is Constructor?

**Our definition**: a constructor is a kind of a function that creates an instance(version) of an object(structure) using the new keyword during the invocation. In layman understanding, a constructor is like a blueprint of how a structure should look.

## Things you must know about a constructor

- It must start with a Capital letter.
- It must be invoked with a ```new``` keyword unless a fallback ```!new.target``` check is internally written by the constructor.
- It must be created using a ```function``` literal and not an arrow function because with the arrow function, these happens:
  1. The Js engine will throw an exception when trying to instantiate it
  2. The ```this``` keyword in arrow functions always reference to the global object(window in browsers, and global in Node) because they have no context of their own.

```js
var name = 'Global'; // We set name on global object here

const obj = {
 name: 'obj', // this name is bind to ```obj```
 getName1: () => {
  this.name = 'getName1'; // unfortunately this is mutating the ```global object```
  return this.name;
 },
 getName2: () => {
  return this.name;
 },
};

console.log('getName1 ', obj.getName1()); // "getName1"

console.log('getName2 ', obj.getName2()); // "getName1"

console.log('Global Affected', this.name); // "getName1"

```

[For more on constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/constructor)

## Code snippet of constructor in js

```js
/**
 * Lets explore js reference and primitive types and prove that they are both objects
 */
const user = {
 name: 'Creative Developer',
 occupation: 'JavaScript Engineer',
};
console.log(user.constructor); //returns a function called Object
console.log(typeof user.constructor === 'function'); // returns true

const str = '';
console.log(str.constructor); //returns a function called String
console.log(typeof str.constructor === 'function'); // returns true

//********************************************************************//
/***
 *@example of javascript built in constructors
 */
//string constructor
const name1 = new String('Creative Developer'); //what this does is basically create an object of strings values out of this string characters
console.log(name1.constructor); //note this is same as the code in line 13🙂.
console.log(name1, typeof name1); //returns an object instead of a string type
console.log(name1.toString()); // "Creative Developer"

const name2 = String('Creative Developer'); //What this does is implicitly do a conversion of this constructor object to its primitive representation aka string
console.log(name2, typeof name2); //returns a string instead of an object type

//********************************************************************//
/***
 *Now lets create our own simple constructor called Person
 *Features of a person: name,age,occupation,gender,actions
 */
function Person(name, age, gender, occupation) {
 //helps to result properly incase user dont want to use the new keyword
 if (!new.target) return new Person(name, age, occupation, gender);

 /**
  * @private property below
  */
 const category = 'Homo sapien';

 /***
  * @public property below
  *
  * @this keyword is basically refering to the Person and the Person is a
  * function but ones we instantiate with new keyword, it becomes a this
  * object. All this magics becomes possible with the new keyword and
  * thats what differentiate a constructor from a regular function
  */
 this.name = name;
 this.age = age;
 this.occupation = occupation;
 this.gender = gender;
 this.myActivities = '';
 this.writersInfo = {};

 /***
  *@public method below
  */
 this.setWhatIDo = function (activities) {
  if (!!activities?.length) {
   this.myActivities = activities.join(', ');
  }
 };

 /***
  *@private method below
  */
 const setWritersInfo = () => {
  this.writersInfo = {
   name: 'Creative Developer',
   occupation: 'JavaScript Engineer',
  };
 };

 setWritersInfo();
}

const person1 = new Person(
 'CreativeAdams',
 20,
 'Male',
 'Sr. Software Engineer'
);
person1.setWhatIDo(['Work', 'Code JS', 'Takwaendo', 'Meditate', 'Sleep']);
console.log(person1);

const person2 = new Person(
 'CreativeJerry',
 19,
 'Male',
 'Sr. Frontend Architect'
);
console.log(person2);

/**
 *@Summary almost all the primitive data-type have their constructor literal
 *that results to an implicit object type.But my sincere advice is never to
 *use a constructor type to create a data when you can easily use its primitive literal.
 *@Note thats not all about the power of constructor, just read on and lets dig deeper
 */

```
