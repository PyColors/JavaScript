# What are the different scopes in JavaScript?

By scope, we mean the lifetime of a variable i.e where that variable is visible and available for programmers to use in their code. 

## 1. Globally scope variables

A global variable:
```javascript
var bar = 10
```

In JavaScript there are a couple of different types of scopes.
Any variables declared outside of any functions, these are termed as global variables and they are available from part of the application itself. Including deeply nested inside of a bunch of other function. You can still access the `bar` variable above in the global scope as long as it has not been redefined in any other scope. 

#### Window object
Another wat to define a global variable, is actually to add it as a property to the `global object window` as we are in a browser. 

Another global variable:
```javascript
window.foo = 4
```

The reason we can use `foo` as a global variable, the same way as we can use `bar` as a global variable is because all global variables are actually properties of the `window object`.

So, `window.foo` will print out `10` into a console because when we defined `bar` as a variable in global scope it automatically added the property of `bar` to the `window object`. This `window object` is only available in browsers. For instance, in `Node.js` this is different, the `global object` in `Node.js` is `Global`.

Note: the global scope of a module is the module itself, so when you define a variable in the global scope of your `nodeJS module`, it will be local to this module. 

More about it in the [NodeJS documentation](https://nodejs.org/api/globals.html#globals_global).


## 2. Function or local scope variables
Another scope which we have in JavaScript is function or local scope variables.

This code below will print `Uncaught ReferenceError: bar is not defined` because, the scope of the variable `bar` is only alive within the block of the function which is defined by the calibraces {}.

```javascript
"use strict"

function foo() {
    var bar = 1;
}
console.log(bar)
```

To correct way to print that code out is add `console.log(bar)` inside the function `foo()` and call it.

```javascript
"use strict"

function foo() {
    var bar = 1;
    console.log(bar)
}

foo()
```

The value of `bar` it's within the function block and visible. 


## 3. Block level scope

From other languages like: **Python**, **Java** or even **C++** the variable `j` and perhaps the variable `i` would only be visible inside the block `for` loop below.
Outside of this block these variables would not be visible.

```javascript
for (var i = 0; i < 10; i ++) {
    var j = 10;
}
```

In fact, in JavaScript, this code below will print out `10`.

```javascript
"use strict"

for (var i = 0; i < 10; i ++) {
    var j = 10;
}

console.log(j)
```

Because, **JavaScript does not have the concept of block level scope**.
Those variables will be available outside of the block level scope.

Also, this for loop is in the global scope so then we are creating global variable `i` and `j` as well.

## Conclusion

There is only two places and two scopes in which variables can exist either: a function scope or a global scope. 
