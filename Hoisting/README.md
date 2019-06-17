# What is variable hoisting?

To describe variable hoisting the best way is with examples:

```
"use strict"

console.log(g);
var g = 10;
```
We are using `"use strict"` it means `g` variable in the `console.log()` has to be declared before it is used.

Most the people would actually expect this code to fail because the variable `g` is been using before it's actually declared and it is declared on the line below.
But if we run through this code no error being print out in the console there's just the `undefined` string is getting printed out from the `console.log(g)` line.

### What is JavaScript doing?

Variable hoisting could be actually a bit confusing, but to understand why `undefined` getting printed out, we have got to understand what JavaScript is doing.

When JavaScript sees some code like `var g` is equal to `10` it actually **splits that out into two lines**. 

The first part is the declaration of `var g` and it will stick that as high as it can *(on the page in this case)* and then it just puts `g` is equal to `10`.

* *Note*: if it’s on the file scope, it will put it on top of the page or, it in the function's scope it will try to put at the top of the function.

```
"use strict"

var g;
console.log(g);
g = 10;
```

That is really what's JavaScript doing:
 Is this split out `var g = 10` to simply `var g` at the top of the file and then `g = 10` at the bottom of the file.
 
When we do `console.log(g)` the variable `g` has already been declared and also a **declared variable which has not been initialized automatically has the value `undefined`**. 

That's what variable hoisting is in JavaScript it's automatic hoisting of the variable declaration to the top its enclosing scope because that code above is in the global scope.

### Inside a function 
If we are inside a function for instance, with the code below, we still have the same behavior.

```
"use strict"

function foo() {
    console.log(g);
    var g = 10;
}

foo();

```

This function going to print out `undefined` because inside a function it still performs the hoisting and only pushes the variable declaration to the top of the function scope, the top of the actual function self. **It won't push it to global scope**.


## Hoist functions themselves

Another example below:

```
"use strict"

foo();

function foo() {
    console.log(g);
    var g = 10;
}
```

Function `foo()` has been called before we have even declared of defined what `foo()` is.
`foo()` is actually declared underneath that statement.

JavaScript is able to call the function `foo()` before it's even seen the function `foo()` and that's because again **JavaScript performs hoisting on functions**.  

So, when JavaScript sees this code it will take any function declaration and move it up to the highest part of the scope that it can find like below: 

```
"use strict"

function foo() {
    console.log(g);
    var g = 10;
}

foo();

```

That is how JavaScript hoists functions.


## Anonymous functions 

Instead of just declaring a function like `foo()` we declare a variable `foo` equal to an anonymous function:

```
"use strict"

foo();

var foo = function() {
    console.log(g);
    var g = 10;
};

```

JavaScript is returning `Uncaught TypeError: foo is not a function`. We might be a bit confused because with the hoisting `var foo...` should be moved to the top of the script and then we would get `undefined` printed as before but that's not the case here.

So, what's happening here? 
JavaScript perform variable hoisting like below:
 
 
```
"use strict"

var foo;

foo();

foo = function() {
    var g;
    console.log(g);
    var g = 10;
};

```

 JavaScript just putting `var` at the top of the scope, variable declaration at the top and then it assigning the anonymous function to the variable `foo()`.
 At this point when we call `foo()` is equal to `undefined` and we can't call `undefined`.
 That's why we are throwing in error: `Uncaught TypeError: foo is not a function`.
 
 
 ### Conclusion
 It's **important** to know and **understand hoisting** in general in JavaScript, function and variable are hoisted to the top of the page, but if we have a variable that's equal to an anonymous function we may be caught out with some of these issues like the example above.
