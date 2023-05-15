## call() :

- Suppose we have an object as follows :

```js
let name = {
  firstname: "Nikhil",
  lastname: "Bagwe",
  printFullName: function () {
    console.log(`${this.firstname} ${this.lastname}`)
  },
}

name.printFullName()
```

- We want a new obj 'name2' with 'printFullName()' function. But it won't be a good practice to write it again in 'name2'.
- So we use call() to borrow function from other objects.
- The concept is known as "Function Borrowing".

## call() example :

- Each every method in JS has access to special function call().

```js
let name = {
  firstname: "Nikhil",
  lastname: "Bagwe",
  printFullName: function () {
    console.log(`${this.firstname} ${this.lastname}`)
  },
}

let name2 = {
  firstname: "Light",
  lastname: "Yagami",
}

name.printFullName.call(name2) // name.printFullName.call(name of obj to which 'this' must be pointed to, argumetns to function if any)
```
- Instead of keeping printFullName() inside an object, we can take it out and use it as below. Also pass arguments.

```js
let name = {
  firstname: "Nikhil",
  lastname: "Bagwe",
}

let name2 = {
  firstname: "Light",
  lastname: "Yagami",
}

let printFullName = function (hometown) {
  console.log(`${this.firstname} ${this.lastname} from ${hometown}`)
}

printFullName.call(name, "Mumbai")

printFullName.call(name2, "Tokyo")
```

## apply() method :

- Only difference between call() and apply() is the way we pass arguments.
- We have to pass a list/array of arguments which the function needs with name of obj.

```js
let printFullName = function (hometown, country) {
  console.log(`${this.firstname} ${this.lastname} from ${hometown}, ${country}`)
}

// printFullName.call(name, "Mumbai")

printFullName.call(name2, "Tokyo", "Japan")

printFullName.apply(name2, ["Tokyo", "Japan"])
```

## bind() method :

- Looks similar to call(). 
- The only diff. is instead of directly calling the printFullName() method, the bind() method binds printFullName() method with a obj and returns us the copy of that method.

```js
let printMyName = printFullName.bind(name2, "Tokyo", "Japan")

console.log(printMyName)

printMyName()
```
- In above example, bind() creates copy of printFullName() and binds it to 'name2' obj and will return a function.
- The catch here is that bind() returned a copy of the function which can be called later.























7
