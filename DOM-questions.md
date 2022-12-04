### event delegation and bubbling

### target(who tiggers the event) vs currentTarget( who listens the event )

### IIFE : immediately invoked function expression
```
(function f() {
alert (0)})()
```
not 
```
function f() {
alert (0)}()
```

### write a function definition or  write a function expression

 -  expression that resolves to a value


### hoisting
all var/function are hoisted
```
function hoisted() {
  if() {

    var me = 'me';
  }
  else {

    var me = 'not me';  ///  do not do this.
  }
  return me;
}

 // the above is explained by js as below:

function hoisted() {
  var me;
  if() {

     me = 'me';
  }
  else {

    var me = 'not me';  ///  do not do this.
  }
  return me;
}

//  so this works 
function hoisted() {
  if() {

     me = 'me';
  }
  else {

    me = 'not me';  ///  do not do this.
  }
  var me;
  return me;
}

```


### null, undefined , undeclared(not defined)

```
let k = p + 1 // p is undeclared

let pp; // undefined

let pp = null; // null
```

### falsy, truthy

```
falsy: ''. 0 , false, null
truthy: [], {}. 1 '1'
```

### check for undfined

```
 p === undefined

 typeof(p) === 'undefined'

```

### check for null

```
typeof(null) === 'object'
k ===  null
```

### == ===

```
null == p  // true
null === p // false 
```

### event loop
- what is the difference between call stack and task queue?


### let vs var
let has block scope
var has function scope
var gets hoited
```
function d(){
  console.log(u); // exception u is not defined

  let u = 0 ;

  console.log(y) // output: 0
  var v = 0 ;
}
```

### compare
```
1 == '1' // true, js has implicited compare functions !!
1 === '1'
```

### let vs const
const cannot be reassign 

### arrow function
 - arrow function use this from the parent scope

```
let profile = {
  firstName: '',
  lastName: ''.
  setName = function (name) {
    const splitName = function() {
      let names = name.split(' ');
      this.firstName = names[0];
      this.lastName = names[1];
    }
    splitName(); // not there is no caller, so what is this, if ther is no onw then gloable this is used
    // bind 
     // let _this = this 
      // _this.splitName()
    // arrow function
     // const splitName = () = > {...}
  }
}

profile.setName('louis Wall');
console.log(profile.firstName);
```

### prototype inheritance

```
// add a new function
Array.prototype.myway =  function () {}
``` 

```
let car = function(mode) {
  this.mode = mode;
}

car.prototype.getMode = function() {
  return this.mode
}
```

### what is promise and why we user it
 - async, waiting for callback function is called
 - promise can resolve value or reject value
 - promise has then/catch/finally functions
  ```
  const p = new Promise( function (resolve, reject) { 
    resolve(12);
    // or 
    reject(34);
  });
  ```

### setTimeout 
 -  wait for ms then call a callback 

```
setTimeout( function(){ 
  console.log(1)
}, 0);
  console.log(2)
  console.log(3)

```

### closure
 - returnning function returns in another function, the returning function will hold its env

```
let fq =  function() {
  let i = 0;
  return {
    setI(k) { // setI will has a closure which has i in it
      i = k
    },
    getI() { // getI will has a closure which has i in it
      return i;
    }
  }
}

let x  = fq();
x.setI(1);

console.log(x.getI(i)); // 1
```
