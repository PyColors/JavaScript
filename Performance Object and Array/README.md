# Performance of JavaScript object and array operations

Before going through what are the relative performance of object and array in JavaScript, let's have a description of what they are.

Arrays and objects are very important concept in JavaScript this is because in JavaScript everything is an object even arrays are special kings of objects. Everything could be made into objects like strings, numbers, boolean, arrays everything is object except the primitive values.  
Note that Objects in JavaScript are not exactly the same thing is objects and some other languages that object-oriented languages.

## What is an Array?
Arrays are simply the place containers holders which could be used to store more than one similar values. For instance, we can create an array in JavaScript with square brackets and supply the values for the array as following:

```javascript
var arrName = [1, 2, 3, 4, 5, 6, 7];
```
Note the index starts from 0 like in every language, that means the first value is 0, the second value is the first value and so on. 
Inside of an array we could put a string, a boolean, a number, we can even put another array and have a nested array. 

## What is an Object?
Objects are very special in JavaScript because everything is object in JavaScript for instance:

```javascript
var myString = "Hello world";
console.log(typeof (myString)); // string
```
This code print out `string`.

But with these next examples below:
```javascript
var myString2 = new String ("Hello world"); 
console.log(myString2); // object
```

```javascript
var myNumber = new Number (3879); 
console.log(myNumber); // object
```

Theses codes here print out: `object`, because in JavaScript whatever we create with the keyword `new` it is automatically assigned as an object in JavaScript.

To create an object we use curly braces as following:
```javascript
var MyObject = {
    object1: 'Hello',
    object2: 'world',
    func: function() {
        return this.object1 + ' ' + this.object2;
    }
};
console.log(MyObject.func()); // Hello world
```
Here we have **keys** values like `object1`, and **properties** value like: `'Hello'`. This is referred to as JSON that stands for JavaScript object notation that is very popular to do APIs.


Note that we can have an array of objects 

## Relative performance of object and array

## Conclusion
