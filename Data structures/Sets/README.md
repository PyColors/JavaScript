# Sets

Sets are one of the most fundamental data structures. The concepts of `set` is simple: it is a group of definite, distinct objects. A `set` in a group of unordered (no duplicate) elements. 
For example, a `set` of integers may be `{1, 2, 3, 4}`. 

Within this, its subsets are `{}, {1}, {2}, {3}, {4}, {1, 2}, {1, 3}, {1, 4}, {2, 3}, {2, 4}, {3, 4}, {1, 2, 3}, {1, 2, 4}, {1, 3, 4},` and, `{2, 3, 4}`.
Sets are important for checking and adding a unique element in **_O(1)_** **constant time**. The reason that sets have constant time operations is that the implementations are based on that of **hash tables**.

Set in natively supported in JavaScript as follows: 
```javascript
var exampleOfSet = new Set ();
``` 

The native `Set object` has only one property: `size` (integer). This property in the current number of element within the `set`. 


## Set Operations
The set is a powerful data structure for performing uniqueness checks. This section will cover the following key operations:
- Insertion
- Deletion 
- Contains

### Insertion
Set has one primary functions: to check for uniqueness. Set **can add items**, but **duplicates are now allowed**.

```javascript
var mySet = new Set();

mySet.add(1); // mySet: Set {1};
mySet.add(1); // mySet: Set {1};
mySet.add(2); // mySet: Set {1, 2};
```
Notice that adding the duplicate element does not work for a set. As mentioned, insertion into a set occurs in constant time.

Time Complexity: **_O(1)_**.

### Deletion

`Set` can also delete items from the set.Set.delete returns a boolean (true if that element exists and was deleted, false otherwise).
```javascript
var mySet = new Set();
mySet.add(1); // mySet: Set {1};
mySet.delete(1); // true
mySet.add(2); // mySet: Set {2};
```

This is useful for being able to delete items in constant time in contrast to arrays where it would take **_O(n)_** time to delete an item.

Time Complexity: **_O(1)_**

### Contains
`Set` has does a quick **_O(1)_** lookup to check whether the element exists within the set.
```javascript
var mySet = new Set();

mySet.add(1); // mySet: Set {1};
mySet.has(1); // true
mySet.has(2); // false

mySet.add(2); // mySet: Set {1, 2};
mySet.has(2); // true
```
Time Complexity: **_O(1)_**.
