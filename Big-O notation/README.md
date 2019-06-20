# What is Big-O Notation

Big-O is a notation used to classify how scalable an algorithm of function is.
And it allows us to estimate the worst case a runtime of an algorithm, or how long it takes the algorithm to complete based on the input size.


So, what this means is that Big O informs us of how much slower an algorithm will run if it's input size grows. If the input size gets a larger say on an array of 2000 elements instead of an array of 60 elements.
- Will the runtime of the function stay the same. 
- Will the runtime get proportionally larger as the input size increases. 
- Will the runtime get exponentially larger. Or will the runtime change in some other way.

This is what Big-O notation tells us, and it describes how performance a function or an algorithm is.
  
## Constant runtime - Big-O Notation: "0 (1)"

If we have a function called log that simply takes in an array and it logs out the first two elements in the array what it's Big O notation or runtime going to be?

The runtime of this function is going to be constant, as 0 of 1 in Big-O notation. We know that the runtime is constant because as the input size increases or in this case, as we increase the size of the array the number of operations that we perform never changes. We still only log out the first two elements no matter how large the array gets. This is called Constant runtime and is written as 0 of 1 in Big-O notation.
We can see this visualized on the graph and as the input size increases the X access, the time that it takes to run the function never changes which is on the y axis.

```
// Constant runtime
// Big O Notation: "0 (1)"

function log(array) {
    console.log(array[0]);
    console.log(array[1]);
}

log([1, 2, 3, 4,]);
log([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
```

## Linear runtime - Big-O Notation: "0 (n)"
Now we have a function called the `logTotal` witch takes in an array and that logs out every element in that array.
What is the runtime of this function?
We know that we have to do an operation on every single element in the array now. So, as the input size increases our runtime, will also increase. For this function our runtime will increase proportionally, to how much our input increases and that makes sense.

If our array has five elements we wil have to perform five operations or log it out five times, if it has six elements we will have to perform sic operations. It it has seven elements we will have to perform seven operations and so on.

This is called linear runtime, because the runtime is proportional to the input and, we write it as 0 of an in Big-O notation. Where O stands for the function we are evaluating and end stands for the size of the input.

```
// Linear runtime
// Big O Notation: "0 (n)"
function logTotal(array) {
    for (var i = 0; i < array.length; i++) {
        console.log(array[i]);
    }
}

logTotal([1, 2, 3, 4, 5]);
logTotal([1, 2, 3, 4, 5, 6]);
logTotal([1, 2, 3, 4, 5, 6, 7]);
```

Let's run through two more run times or time complexity as there are very often seen throughout engineering and programming.


## Exponential runtime - Big-O Notation: "0 (n^2)"
The next runtime that we will explore is exponential runtime.

```
// Exponential runtime
// Big O Notation: "0 (n^2)"
function addAndPrint(array) {
    for (var i = 0; i < array.lengtht; i++) {
        for (var j = 0; j < array.lengtht; j++) {
            console.log(array[i] + array[j]);
        }
    }
}

addAndPrint(['A', 'B', 'C']);            // 9 pairs logged out
addAndPrint(['A', 'B', 'C', 'D']);       // 16 pairs logged out
addAndPrint(['A', 'B', 'C', 'D', 'E']);  // 25 pairs logged out
```

So, now we have a function called `addAndPrint` which takes in an array. What it does is it gives us every possible combination of pairs in the array and iterates through the whole array and every element that it hits it goes through the whole array and hits on every element again. All possible pairs are made.
That's why we have two nested `for` loops here.

For example: if we have an array of three elements we have nine pairs that are logged out and if we an array of four elements we get 16 pairs logged out and so on.
This is exponential as we add one element to the input. The runtime makes an exponential jump. We can this visualize on the graph and we can tell that this is not very efficient in performance.

If a programmer write a function like this in his code he probably won't be able to notice the performance issues with very small inputs. But as the inputs start to scale and become very large a function with exponential time complexity becomes very inefficient and can slow down in application.

So, we try to stay away from creating functions that have this runtime as much as possible and, exponential runtime is written as O of and squared (n^2) in Big O Notation.


## Logarithmic runtime  - Big O Notation: "0 (log n)"
Now the final runtime that we will explore is logarithmic runtime and it is very performance.
An example of a logarithmic algorithm is **binary search** and we can see the code for this below:

```
// Logarithmic runtime
// Big O Notation: "0 (log n)"
function binarysearch(array, key) {
    var low = 0;
    var hight = array.lenght -1;
    var mid;
    var element;
    
    while (low <= hight) {
        mid = Math.floor((low + hight) / 2, 10);
        element = array[mid];
        
        if (element < key) {
            low = mid + 1;
        } else if (element > key) {
            high = mid - 1;
        } else {
            return mid;
        }
    }
    return -1;
}
```

Instead of running though this code let's think about it conceptually, in any binary search algorithm, we will have tow inputs.
One is a list that must be sorted in some way either numerically from least to greatest or from Greatest To least of alphabetically ect. Has to be sorted in some way.

And our other input (key) is simply just a single value that we want to try and search for within our array. 

Binary search has a logarithmic runtime because with every operation that we perform we are cutting the input in half. This is great because even if we have a **huge input** we are only going to be **looking at a fraction of the elements** to find the one that we are **searching for**.

Binary search is an example of a logarithmic runtime or time complexity, witch is written as all of a log and in Big-O notation and you can see it depicted on our graph.

![](http://www.pycolors.com/v2/git/Big-0/Big-O-Notation.png)
