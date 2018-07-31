Below are notes I took along the way of things I wanted to remember most when reading this series. You may also see code snippets of me practicing things as well, usually in some way related to a project I'm working on.

# Chapter 1: What is Scope?
Parts involved in scoping 'conversation':
 - Engine
 - Compiler
 - Scope

> To summarize: two distinct actions are taken for a variable assignment: First, Compiler declares a variable (if not previously declared in the current scope), and second, when executing, Engine looks up the variable in Scope and assigns to it, if found.

> When Engine executes the code that Compiler produced for step (2), it has to look-up the variable a to see if it has been declared, and this look-up is consulting Scope. But the type of look-up Engine performs affects the outcome of the look-up.

Engine can perform LHS (Left-hand side or, "who's the target of the assignment") or RHS (right-hand side or, "who's the source of the assignment") look-ups.
 - LHS look-ups are for assignments (`a = 2;`)
 - RHS look-ups are for getting value (`console.log(a);`)

## Example
 ```javascript
 function foo(a) {
     console.log(a);
 }

 foo(2);
 ```

  - `foo(..)` and `console.log(a);` are RHS look-ups.
  - `a = 2` is a LHS look-up.


## Quiz: Identify the LHS and RHS look-ups
 ```javascript
function foo(a) {
	var b = a;
	return a + b;
}

var c = foo( 2 );
 ```
 1. Identify all the LHS look-ups (there are 3):
    1. Engine asks Scope for c (`var c =`)
    2. Engine asks Scope for a, then assigns a to 2 (implied `a = 2`)
    3. Engine asks Scope for b, then assigns b to a (`var b =`)
2. Identify all the RHS look-ups (there are 4):
    1. Engine asks Scope for foo (`foo( 2 );`)
    2. Engine asks Scope for a (`= a`) **Note: Engine doesn't care what b was previously, only if it exists so it can assign a into b.**
    3. Engine asks Scope for a, again (`a +`)
    4. Engine asks scope for b, again (`+ b`)


# Chapter 2: Lexical Scope
