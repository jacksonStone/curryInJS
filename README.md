# CurryInJS
Micro-library for adding the capacity for javaScript functions to be curried.

```javascript
var curry = Curry.curry;
var func = curry(function(a,b,c){
    console.log(a,b,c);
  });
  
//Can call like this
func(1)(2)(3); // 1,2,3
//or
func(1, 2)(3); // 1,2,3
//or something like this:
var func1 = func(1,2); //a function waiting for 1 argument
func1(3); // 1,2,3
func1(4); // 1,2,4
```

If you wish to hard code the number of arguments a function is waiting for you can.

```javascript
console.log = curry(3, console.log);
//console.log is now "waiting" for 3 arguments before it executes.
console.log(1)(2)(3) // 1,2,3
```

If you've made the mistake of using the "this" keyword, don't worry. _This_ can also be taken care of.

```javascript
var curryThis = Curry.curryThis;

var e = {
  a:1, 
  b:function(c,d){return console.log(this.a,c,d)}
}

var newFunc = curryThis(e, 'b');

newFunc(2,3); // 1,2,3

```

If you need arguments to go right to left, rather than left to right, I've got something for you too!

```javascript
var curryR = Curry.curryR;

var backwardsFunc = curryR(function(a,b,c){console.log(a,b,c)});
backwardsFunc(1,2,3); // 3,2,1
backwardsFunc(1)(2,3); // 3,2,1

```
