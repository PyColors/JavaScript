# What are the different type in JavaScript?

ECMAScript 5, the specification defines six different types in JavaScript. We have **five primitives types** and **one non-primitive type**.

In terms of the primitive type we have:


| Primitive type | values |
| ------ | ------ |
| Boolean | `true` or `false` |
| Number | It could be an integer: `1` or double: `4.5`  |
| String | Both double quotes or single quotes: `"b"` or `'b'` |
| Null | It could be the type: `null` |
| Undefined | It could be the type: `undefined` |



And our non-primitive type:

| non-primitive type | values |
| ------ | ------ |
| Object | Special curly braces notation : `{}` or instantiating an object: `new Object()` |

So, those are the types that we have in JavaScript.


# There is a function in JavaScript called `typeof` to be able to print out the type of a value.

| Values | Types |
| ------ | ------ |
| `typeof(2)` | `number` |
| `typeof('b')` | `string`  |
| `typeof(trus)` | `boolean` |
| `typeof(undefined)` | `undefined` |
| `typeof(null)` | `object` which incorrectly, is actually the typeof object. The `typeof` null is actually null. This a problem in JavaScript, the change can't really be reversed now without causing a number of problems. | 
| `typeof({})` | `object` |

So, those are the different types we have available to use in JavaScript.



# Difference between undefined and null

Tow types that represent the concept of no value;
`undefined` it's used by the JavaScript engine to inform developers that this is either an uninitialized variable, it's either a parameter that's missing from the function parameters list or it's perhaps an unknown property of an object.

`null` is usually used by programmers to indicate no value. JavaScript engine will never set a value to null for developers it will always set it to undefined if it does not know what it is.
`undefined` is used by JavaScript and means no value. It's used for:
- Uninitialized variables.
- Missing parameters to functions.
- Unknown variables and unknown properties related the window object


