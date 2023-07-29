# Core OOP in JavaScript - 1st Edition

# Chapter 1: Pillars of OOP

# Abstraction

## What is Abstraction?

Abstraction is a way of hiding away the logic from the user and living them with only the functionality(aka function/methods). I call abstractions a façade,

## Important note about Abstraction

- It looks like other constructors(class), but you can never instantiate it with a new keyword.
- It aimed at reducing code duplication, i.e it can be extended to many other consumer-constructor.


## Code snippet of Abstract constructor in JavaScript es5

```js
/**
 * Abstract constructor
 */
function Human() {
  /***
   * The below error exception throws when we try to
   * instantiate the Abstract constructor.
   */
  throw new Error("Sorry, an Abstract constructor is not instantiable ⚠️.");
}


Human.prototype.legs = 2;
Human.prototype.hands = 2;
Human.prototype.specie = "Homo Sapien";

/**
 * A normal constructor(class) below that will use the
 * methods of Human through a pattern called copying-extension
 */
function Ladies(name) {
  if (!new.target)  return new Ladies();
  
  this.name = name;
}

/***
 * This is where we extend the methods of Human Abstract-constructor into Ladies constructor
 * 
 * @Explanation: so what we doing here is deriving the "public"
 * contents of Human constructor into an unenumerable object using
 * Object.create, and then taking those contents(public properties and
 * methods) into the Ladies.constructor using the "prototype" object.
 * To read more about prototype object, read the file dedicated to it.
 */
Ladies.prototype = Object.create(Human.prototype);

//Now lets add more methods to the Ladies constructor
Ladies.prototype.getLadiesComplement = function () {
  return `My name is ${this.name}, and i am a beautiful lady with ${this.legs} legs and ${this.hands} hands of the ${this.specie} specie.`;
};

const ladies = new Ladies("Anastesia");
console.log(ladies); //As you can see, the extended methods and properties
//from Human are physically hidden away from the instantiated
//constructor(they are placed inside the Ladies prototype object)
console.log(ladies.getLadiesComplement());

/***
 * Now lets break everything by trying to instantiate the Abstract constructor(class)⚠️
 */
const human = new Human();
```
