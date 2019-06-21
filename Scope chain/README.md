# What is the scope chain?

The scope chain is defined by the way the **program is written in the file**. 
So the best way to explain this is with a couple of examples.

## The scope chain is defined
```javascript
"use strict"

function foo() {
    console.log(myvar)
}

function bar() {
    var myvar = 8;
    foo();
}

bar()
```

This code will print out `Uncaught ReferenceError: myvar is not defined`.
The reason for that is that the scope chain is defined, what's called `Lexically`. That's means the scope chain is defined in the order in which the code is written on the page or in the file.

So, `myvar` variable isn’t available to the `bar()` function because literary in the file, the `myvar` variable isn't declared above the `foo()` function.


## Lexically defined
Another wat to explain this with that code below by putting the `foo()` function inside the `bar()` function:


```javascript
"use strict"

function bar() {
    var myvar = 8;
    function foo() {
        console.log(myvar)
    }
    foo();
}

bar()
```
Now, when we run this code `8` is printed out. That's because **the scope chain is lexically defined** so when the inner  `foo()` function's called and it looks for `myvar` it's then going to look inside its own scope: which is`{ console.log(myvar) }`.

Obviously, it's not going to find the `myvar` function, so it's going to look in the outer scope which is`bar()` function and, finds finally the `myvar` variable.


## Global scope last level

What will happening if we move `var myvar = 8;` outside the `bar()` function in the Global scope?

```javascript
"use strict"

var myvar = 8;
 
function bar() {
    function foo() {
        console.log(myvar)
    }
    foo();
}

bar()
```

When we run through this code above `8` is getting printed out with this change. The `foo()` function is getting called, it's going to look for `myvar` it can't find it inside it's own scope, so it looks in its outer scope which is the `bar()` function it can't find it in `bar()` function scope, so it looks in the global scope and there, it finds it.

### Conclusion:

It's important to know how JavaScript resolves a variable an in it looks inside its inner scope and then the outer scope until it finds the variable. 
And understanding of **the lexical nature of the scope chain**, that is to say, that the scope chain is defined by **how the code is physically written on the page** versus **how the functions are called**.
