# What are function closures?

Closures can seems pretty complex. 

## 1. Basic

This function below return a function which then prints out a name. `sayHello` function actually returns a function and inside that function, `text` will print out.
```javascript
"use strict";

function sayHello(name) {
    var text = 'Hello ' + name;
    return function() {
        console.log(text);
    }
};

var sayWelcom = sayHello("Welcom")
sayWelcom();
```

When `sayWelcom` has been invoked the return function print out the text variable, but according to the [scope rules](https://github.com/PyColors/JavaScript/tree/master/Scopes#what-are-the-different-scopes-in-javascript), as soon as `sayHello` exits, any variables declared inside it go out of scope and are deleted.

Anything declared internally inside sayHello scope `(var... and return..)` should actually be deleted as soon as the `sayHello` function has finished and executed.

**But one exception for that is with closures**. When a function returns a function as the `sayHello` function is doing, it's returning a function. 
The function that's returned then **keeps a reference to any variables that it needs to execute**. So it's using the `text` variable, it keeps a reference to the variable.

That's what a closure is, it's a special set of references to variables that a function needs in order to execute. *Variables that are outside of this function scope*.

Closures can refer to variables in outer scopes and scope's external to itself.
Since the return function been returned by another function it's going to be a closure and it can refer to variables in scopes outside of itself in outer scopes. So it's referring to variables in its outer scope which is in the scope of `sayHello` function.  

### Closure points to the common value

```javascript
"use strict";

var foo = [];
for (var i = 0; i < 10; i ++) {
    foo[i] = function() { return i };
}

console.log(foo[0]());
console.log(foo[1]());
console.log(foo[2]());
```
We may expect the output of this code above could be `0, 1, 2` but it's actually: 
```javascript
10 
10
10
```

Because, when `console.log(foo[0]())` was created, when this `function() { return i }` was created `i` used to be zero.

When the closure is created is **does not get a copy of `i` so the closure isn't a copy of `i`**. This closure points to the actual value of `i` in the outer scope.
By the time `console.log(foo[0]())` has been called, the `for` loop has been exhausted and `i` is then ten.
Closure just points to the common value of whatever variables are used in its function body, the current value.


## 2. Implement the correct behavior

To actually be able to return this output below, we can join forces with an IIFE, and use them both together to solve this problem.
```javascript
0
1
2
```

Add an IIFE: *Immediately Invoked Function Expressions*:

```javascript
"use strict";

var foo = [];

for (var i = 0; i < 10; i++) {
    (function() {
        var y = i;
        foo[i] = function() {
            return y
        };
    })();
}

console.log(foo[0]());
console.log(foo[1]());
console.log(foo[2]()); 
```

Now, for each loop through we are going to execute this immediately invoked function. A function has its own internal scope so when the new IIFE function gets called, a new variable called `y` has been created, we assign that variable to whatever the value of `i` was at that moment.

We are just returning `y` instead of `i` in that closure. As an example and see it, put a breakpoint on `return y` line to see the result in closure section with google chrome dev tools. 

We can see this like snapshoting whatever values we needs for that closure at that moment in time.



## 3. Cleaner way, primitive types 

There is another way to solving this problem and have the same output as well.

```javascript
"use strict";

var foo = [];

for (var i = 0; i < 10; i++) {
    (function(y) {
        foo[y] = function() {
            return y
        };
    })(i);
}

console.log(foo[0]());
console.log(foo[1]());
console.log(foo[2]()); 
```

Primitive types in JavaScript are passed by value not by reference. 

The `y` is not referring to the same `i` variable in its outer scope, it's actually a copy. When we use `y` and we return `y` we're returning the copy of `y` with the IIFE.


## Conclusion: 
Closure points to the current value of that outer scope variable, not the value of that outer scope variable when that closure was created.
