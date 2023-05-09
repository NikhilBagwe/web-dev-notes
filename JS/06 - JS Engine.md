## JavaScript Runtime Environment :

- JRE is like a big container which has all the things required to run JS code.
- It has a JS Engine, set of APIs to connect/access to the outer environment, Event loop, Callback queue, Microtask queue.
- Every browser has JRE.
- Similarly any device that has JRE can run JS. Thus, JS runs on many devices.
- We can even create our own JS engine by following ECMAScript standards.

## List of JS engines :

- Edge : Chakra
- Chrome : V8 engine (Written in C++)
- Firefox : SpiderMonkey ( First ever JS engine created, by Brendon, creator of JS)

## JS Engine Architectire :

- It takes the JS code that we write as i/p.
- This code then goes through 3 major steps : Parsing, Compilation and Execution.

### Parsing phase :

- In this phase the JS code is broken down into 'Tokens'.
- Then the 'Syntax Parser' coverts the tokens into AST (Abstract Syntax Tree).

### NOTE : JS can behave as a Compile as well as Interpreted language. It all depends on the JS engine.

### Compilation and Execution phase :

-  Initially JS was suppposed to be Interpreted language as browsers cannot wait for the whole code to get compiled and then execute it.
-  But nowadays, the Modern browsers use Compiler + Interpreter together called as JIT compilation.
-  So the AST goes to the Interpreter. It converts it to byte code and sends it for execution. While it is doing so it takes help of 
compiler to optimize the code.




















90
