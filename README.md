
#30 days of Javascript 

 - [30-days-of-javascript](https://leetcode.com/studyplan/30-days-of-javascript)
Following a leetcode series of 30 Javascript question.


## Day 1 
###### Write a function createHelloWorld. It should return a new function that always returns "Hello World".

```javascript
const createHelloWorld = () => {
    
    return (...args) => {
     return "Hello World";   
    }
};
```
## Day 2 
###### Given an integer n, return a counter function. This counter function initially returns n and then returns 1 more than the previous value every subsequent time it is called (n, n + 1, n + 2, etc).

```javascript
const createCounter = (n) => {
    return () => {
    return n++ ;
    };
};
```
## Day 3 
###### Write a function expect that helps developers test their code. It should take in any value val and return an object with the following two functions.

toBe(val) accepts another value and returns true if the two values === each other. If they are not equal, it should throw an error "Not Equal".
notToBe(val) accepts another value and returns true if the two values !== each other. If they are equal, it should throw an error "Equal".

```javascript
const expect = (val) => {
    return {
toBe :(val2) => {
        if(val === val2) return true;
    else throw new Error("Not Equal");
},
    notToBe: (val2) => {
        if(val !== val2) return true;
    else throw new Error("Equal");
    
}}
};
```
## Day 4 
###### Write a function createCounter. It should accept an initial integer init. It should return an object with three functions.

The three functions are:

increment() increases the current value by 1 and then returns it.
decrement() reduces the current value by 1 and then returns it.
reset() sets the current value to init and then returns it.

```javascript
const createCounter = (init) => {
    let temp = init;
    return{
        increment:()=>{
            return ++init ;
        },
            decrement:()=>{
            return --init;
        },
            reset:()=>{
                return init =  temp;
            };
    }
};
```
## Day 5 
###### Given an integer array arr and a mapping function fn, return a new array with a transformation applied to each element.

The returned array should be created such that returnedArray[i] = fn(arr[i], i).

Please solve it without the built-in Array.map method.

```javascript
const map = (arr, fn) => {
const newArr = [];
  for (let i = 0; i < arr.length; i++) {
    newArr.push(fn(arr[i], i));
  }
  return newArr;
};
```
## Day 6 
###### Given an integer array arr and a filtering function fn, return a filtered array filteredArr.

The fn function takes one or two arguments:

arr[i] - number from the arr
i - index of arr[i]
filteredArr should only contain the elements from the arr for which the expression fn(arr[i], i) evaluates to a truthy value. A truthy value is a value where Boolean(value) returns true.

Please solve it without the built-in Array.filter method.

```javascript
const filter = (arr, fn) => {
    const filteredArr = [];
    
    for(let i = 0; i < arr.length; i++){
       if (fn(arr[i], i, arr)) {
            filteredArr.push(arr[i]);
        }
    }
    return filteredArr;
};
```
## Day 7 
###### Given an integer array nums, a reducer function fn, and an initial value init, return the final result obtained by executing the fn function on each element of the array, sequentially, passing in the return value from the calculation on the preceding element.

This result is achieved through the following operations: val = fn(init, nums[0]), val = fn(val, nums[1]), val = fn(val, nums[2]), ... until every element in the array has been processed. The ultimate value of val is then returned.

If the length of the array is 0, the function should return init.

Please solve it without using the built-in Array.reduce method.

```javascript
const reduce = (nums, fn, init) => {
    if(nums.length === 0) return init;
    let val = init;
    for(let i = 0;i < nums.length;i++){
        val = fn(val,nums[i])
    };
    return val;
};
```
## Day 8 
###### Given an array of functions [f1, f2, f3, ..., fn], return a new function fn that is the function composition of the array of functions.

The function composition of [f(x), g(x), h(x)] is fn(x) = f(g(h(x))).

The function composition of an empty list of functions is the identity function f(x) = x.

You may assume each function in the array accepts one integer as input and returns one integer as output.

```javascript
const functionComposition = (functions, x) => {
    if (functions.length === 0) {
        return x; // Identity function
    }

    // Start with the rightmost function
    let result = functions[functions.length - 1](x);

    // Compose functions from right to left
    for (let i = functions.length - 2; i >= 0; i--) {
        result = functions[i](result);
    }
    return result;
};

```
## Day 9 
###### Write a function argumentsLength that returns the count of arguments passed to it.

Example 1:

Input: args = [5]
Output: 1
Explanation:
argumentsLength(5); // 1

```javascript
const argumentLength = (...args) => { return arguments.length };
```
## Day 10 
###### Given a function fn, return a new function that is identical to the original function except that it ensures fn is called at most once.

The first time the returned function is called, it should return the same result as fn.
Every subsequent time it is called, it should return undefined.

```javascript
const once = function(fn) {

  let hasBeenCalled = false;
  let result;

  return function(...args) {
    if (!hasBeenCalled) {
      result = fn(...args);
      hasBeenCalled = true;
      return result;
    } else {
      return undefined;
    }
  }

};
```
## Day 11 
###### Given a function fn, return a memoized version of that function.

A memoized function is a function that will never be called twice with the same inputs. Instead it will return a cached value.

```javascript
const memoize = (fn) => {
    let memo = {};
    
    return (...args) => {
        let key = JSON.stringify(args);
        if( key in memo){
            return memo[key];
        }else{
             let temp = fn(...args);
            memo[key] = temp;
            return temp;
        }
    }
}
```
## Day 12 
###### Given two promises promise1 and promise2, return a new promise. promise1 and promise2 will both resolve with a number. The returned promise should resolve with the sum of the two numbers.

```javascript
const addTwoPromises = async (promise1, promise2) => {
      const [value1, value2] = await Promise.all([promise1, promise2]);
  return value1 + value2;
};
```

## Day 13 
###### Given a positive integer millis, write an asynchronous function that sleeps for millis milliseconds. It can resolve any value.

```javascript
async function sleep(millis) {
     return new Promise((resolve, reject) => { setTimeout(() => { console.log("hello"); resolve(200); }, millis); });
}
```
