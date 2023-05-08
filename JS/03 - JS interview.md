## 1. Explain closure and Double Parenthesis example

- A function bundled with it's lexical scope.
- Each function in JS has access to its lexical environment.
- So even when 'inner()' function is executed in other scope, it still remains its lexical env where it was originally present in the code.

```js
function outer() {
  var a = 10
  function inner() {
    console.log(a)
  }

  return inner
}

outer()() // similar to "var z = outer(); z();"

```
- Even when 'var a = 10' is moved down, it will still work.

```js
function outer() {
  function inner() {
    console.log(a)
  }
  var a = 10

  return inner
}

outer()()
```

## 2. Can we use 'let' declarations to form a closure.

- Yes, it will still work the same way.
- inner() will still form a closure.

```js
function outer() {
  let a = 10
  function inner() {
    console.log(a)
  }

  return inner
}

outer()()

```

## 3. Does the parameter we pass in outer() func become part of closure.

- Yes, since inner() func forms a closer with its outer() env and param 'b' is also part of it.

```js
function outer(b) {
  let a = 10
  function inner() {
    console.log(a, b)
  }

  return inner
}

outer("Hello")() // 10 'Hello'
```

## 4. Will closure work on nested functions.

- Yes

```js
function outest() {
  var c = 100
  function outer(b) {
    let a = 10
    function inner() {
      console.log(a, b, c)
    }

    return inner
  }
  return outer
}

var closure = outest()("Hello")
closure()  // 10 'Hello' 100
```

## 5. What if there are conflicting Global variable names ?

- The inner() func will still referenece to 'a = 10'.
- In case, line 'a = 10' was not present, then inner() might have went to global environment to find 'a', where 'a = 20' is present and printed it.

```js
function outest() {
  var c = 100
  function outer(b) {
    let a = 10
    function inner() {
      console.log(a, b, c)
    }

    return inner
  }
  return outer
}

let a = 20

var closure = outest()("Hello")
closure()
```

## 6. Data hiding and Encapsulation :

- Used to make sure nobody in the program can directly access a certain variable/function.

```js
function counter() {
  // 'count' is hided and can only be accesed through incrementCounter()
  var count = 0
  return function incrementCounter() {
    count++
    console.log(count)
  }
}

var counter1 = counter()
counter1() // 1
counter1() // 2
```
- In above example, if we create a new 'counter2' than it will be a fresh counter. It won't affect the values of counter1.
- The 'incrementCounter() func will form a closure with new independent copy of 'count'.

```js
function counter() {
  // 'count' is hided and can only be accesed through incrementCounter()
  var count = 0
  return function incrementCounter() {
    count++
    console.log(count)
  }
}

var counter1 = counter()
counter1() // 1
counter1() // 2

var counter2 = counter()
counter2()
counter2()

```

## 7. Function Constructor :

- In above counter example, the way we coded it is not a good scalable way of writing code.
- So use Function Constructor.

```js
function Counter() {
  // still the data is hidden
  var count = 0

  this.incrementCounter = function () {
    count++
    console.log(count)
  }
  this.decrementCounter = function () {
    count--
    console.log(count)
  }
}

var counter1 = new Counter()
counter1.incrementCounter()
counter1.incrementCounter()
counter1.decrementCounter()

```
- Still a closure is formed and our data is hidden.

## 8. Disadvantages of closures :

- Over-consumption of memory - As the variables in lexical env. of function are not garbage collected, thus accumulating a lot of memory.
- If not handled properly, than can lead to memory leaks.

## 9. What is Garbage collector :

- It is a program in the browser or JS engine which frees up the unutilized memory.
- In programming languages like C/C++, it is upto developer to allocate/deallocate memory. 
- But in high level prog. lang. like JS we have garbage collector.

## 9. Relation between Closure and Garbage collector :

```js
function a() {
  var x = 0
  return function b() {
    console.log(x)
  }
}

a()
```
- So normally when execution of a() is completed, 'var x' could be garbage collected as it is no longer needed.
- But since, we have b() referencing 'var x' forming a closure, 'var x' won't be deleted.


## 10. Smart garbage collection mechanism :

- Modern browsers such as chrome V8 have smart garbage collection mechanism.
```js
function a() {
  var x = 0, z = 10
  return function b() {
    console.log(x)
  }
}

a()
```
- In above eg. even though 'var z' forms closure with b(), it will be deleted as it is not used in func b().

















0
