## Intro :

```js
function x() {
  var a = 7
  function y() {
    console.log(a)
  }
  y()
}

x()
```

- In above example, y() first tries to find 'a' inside it's local memory store. 
- Since it's not present their, it goes to find 'a' in it's lexical parent's memory where it finds 'a=7'.
- Thus it logs '7' as o/p.
- This is what a Closure is.

## Closure :

- A Closure is a function bind together with it's lexical environment.
- It is a function along with it's lexical scope that forms a closure.

## Returning a function :

- In below example, we are returning func y() once x() is executed.
- So here x() is removed out of global execution context. So technically we cannot access 'var a' now as its deleted.

```js
console.log("Program starts")

function x() {
  var a = 7
  function y() {
    console.log(a)
  }
  return y
}

var z = x()
z()

console.log("program ends")
```
- But now when you execute 'z()', it will o/p '7'.
- This is where real use of CLosure can be observed. 
- The 'func y()' is returned with it's lexical scope (i.e a Closure) where in 'var a' is present even after x() is deleted.
- So whenever we execute 'z()' anywhere in our pgm, it will still remember it's lexical scope.
- We can also directly return the 'func y()' also as below.

```js
function x() {
  var a = 7

  return function y() {
    console.log(a)
  }
}
```

## Closure Corner cases :

### CASE 1 :

- In Closure, the function remembers the reference to the variable in it's lexical scope.
- So in below example even if value of 'a' was updated, func y() will remember the refernece to 'a' and thus 100 is printed.

```js
console.log("Program starts")

function x() {
  var a = 7
  function y() {
    console.log(a)
  }
  a = 100

  return y
}

var z = x()
z()

console.log("program ends")
```

### CASE 2 : Lexical scope of parent, parent of current parent and so on is also maintained.

- The variable 'a and b' are not garbage collected when their function's execution is finished and thus returned as a closure.

```js
console.log("Program starts")

function z() {
  var b = 1000
  function x() {
    var a = 7
    function y() {
      console.log(a, b)
    }

    y()
  }
  x()
}

z()

console.log("program ends")
```

## Use cases of Closure :

- Module Design pattern
- Currying
- A function which can be executed only once - by making it remember it how many times it was executed.
- Memoize
- Maintaining state in async world
- setTimeouts
- Iterators






3



