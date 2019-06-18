# Does JavaScript pass parameters by value or by reference?

## Pass-by value

What this means is that if we change the value of a **primitive type inside a function**, the changes **won't affect the variable in the outer scope**.
For example:

```
"use strict"

var c;

function foo() {
    // Do something
}
```
The `var c` in this code above is the **outer scope** and inside the function is the function scope or the inner scope.


Now, let's add `var c = 10`, *`10` is a primitive type* and call the `c function`:

```
"use strict"

var c = 10;

function foo(c) {
    // Do something
}
foo(c);
console.log(c)
```

`c` will be print out 10 because `c` is equal to 10 on the top.

But if within the `foo()` function we change `c` to `14` by adding `c = 14` and print out this.

```
"use strict";

var c = 10;
function foo(c) {
    c = 14;
}
foo(c);
console.log(c);
```
It's still printing out `10`, that's because for **primitive types** when they are passed into to `foo()` there are passed by **value**.

Pass by value means is that really is **passing a copy** of `var c`, so anything we do to `c` **inside the body of the function won't affect `var c`**, because we passed a **copy of the initial value** of `var c`: 10.
That even is valid if we have **another primitive** type like boolean:

```
"use strict";

var c = true;
function foo(c) {
    c = false;
}
foo(c);
console.log(c);
```

Now, `c` is equal to `true` and then `c` to `false` inside the body function it will **still print** `true`, because again `c` is a primitive and when `c` gets passed to a function we pass in a **copy of `c`**.

### That's pass-by value. What is pass-by reference?

## Pass-by reference

When we are passing something by reference we're passing something that point to something else, versus a copy of the object.

So, since with **JavaScript** passing in an object **passes it by reference**, when we **change a property of that object** from within the function, **the change will be reflected in the outer scopes**. Let's have an example with the previous code and some changes.

```
"use strict";

var c = {};
function foo(c) {
    c.phone = false;
}
foo(c);
console.log(c);
```
When we're logging `c` it's logging an object with `phone` is equal to `false` with a key of `phone` and a value of `false`.
That's because `c` is now an object, when we **pass an object into a function** we are **not passing in a copy**, we're actually passing in something that points, that really does **point to the `c` object**.

So, when we change a property of `c.phone` object we're actually are **changing a property** of the `c` object in the **outer scope**.
That's why we are printing out the `c` object with the **changes** from the `foo()` **function applied**.


However, let's **change a little bit the code** by `c` to `{'bar': 'foobar'}` and then within the function instead of changing a property of `c` let's adding **exactly what `c` pointed** by: `{'bar': 'foo'}`.
```
"use strict";

    var c = {'bar': 'foobar'};

function foo(c) {
    c = {'bar': 'foo'};
}
foo(c);
console.log(c);
```

This code printing out `{bar: "foobar"}` which is the **value of the variable `c`** in the **outer scope** and not what the body function **tried to replace** `c` with.

In JavaScript when we say we **pass-by-reference**, we can't then change what `c` points to. We can only change a property of `c` to something else or **add a property** or **change a property**.


## Conclusion

JavaScript passes primitives types such as **strings, numbers, and boolean by value** and it **passes objects by reference**.
