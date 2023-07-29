# Core OOP in JavaScript - 1st Edition

# Chapter 2: What is OOP?

OOP stands for Object Oriented Programming

## OOP Keywords

**- Object**: According to the Oxford dictionary, it's a person or thing to which a specified "action" or "feeling" is directed.

**- Oriented**: According to [vocabulary.com](https://www.vocabulary.com/), to be oriented is to be positioned in a direction relative to something or someplace else, and it's often used with the prepositions "toward" or "away from.

**- Programming**: According to Wikipedia, Computer programming is the process of designing and building an executable computer program to accomplish a specific computing result or to perform a specific task.

## Our Definition

OOP is a type of programming where a computer program is structured to have specific properties and actions and how it must be used to accomplish a task.

## OOP Illustration

### Lets write an object of a person

```js
const person1 = {
    name: "Emmanuel Onah",
    age: 20,
    occupation: "JavaScript Engineer"
}
```

## Four Pillars of OOP

**- Abstraction**: This is a code pattern where you abstract a logic from the consuming function(its like a façade).

**- Encapsulation**: This is a code pattern used to restrict the access of a code.

**- Inheritance**: This is a code pattern where the properties and methods of one object(constructor) get acquired by another object(constructor) without redefinition.

**- Polymorphism**: This is a concept where the same action is performed in a different form(this is usually possible by having a base constructor whose content gets injected into another constructor prototype, and the result overridden).

## Summary

In summary, you can see an OOP as a residential form you fill whenever you change your apartment. A residential form has different fields and some fields are static and can never change(per se, those fields are filled by the administrator).
[For more on OOP in JS](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object-oriented_JS)

## Code snippet of Car Object

```js
/***
 * The below code is a custom object oriented program of a car
 */
function Car(name) {
 //this helps to result to the same behaviour if user don't invoke the constructor with the new keyword
 if (!new.target) return new Car(name);

 this.name = name;
 this.doors = 4;
 this.defaultSpeed = '30 kmph';
}

Car.prototype.getSpeed = function getSpeed() {
 switch (this.name) {
  case 'Tesla':
   return `${this.name} speed is 200 kmph`;

  case 'Mercendez':
   return `${this.name} speed is 130 kmph`;

  case 'Toyota':
   return `${this.name} speed is 80 kmph`;

  default:
   return `${this.name} speed is `.concat(this.defaultSpeed);
 }
};

const car_1 = Car('Tesla');
console.log(car_1.getSpeed());

const car_2 = Car('Mercedes');
console.log(car_2.getSpeed());

const car_3 = Car('Toyota');
console.log(car_3.getSpeed());

const car_4 = Car('EmmaTex');
console.log(car_4.getSpeed());
```
