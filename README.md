
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
