Scope determines the accessibility (visibility) of variables.

JavaScript has 3 types of scope:

-   Block scope
-   Function scope
-   Global scope


## Block Scope

Before ES6 (2015), JavaScript had only **Global Scope** and **Function Scope**.

ES6 introduced two important new JavaScript keywords: `let` and `const`.

These two keywords provide **Block Scope** in JavaScript.

Variables declared inside a { } block cannot be accessed from outside the block:

```js
{  
  let x = 2;  
}  
// x can NOT be used here
```

Variables declared with the `var` keyword can NOT have block scope.

Variables declared inside a { } block can be accessed from outside the block.

```js
{  
  var x = 2;  
}  
// x CAN be used here
```

## Local Scope

Variables declared within a JavaScript function, become **LOCAL** to the function.

```js
// code here can NOT use carName  
  
function myFunction() {  
  let carName = "Volvo";  
  // code here CAN use carName  
}  
  
// code here can NOT use carName
```

Since local variables are only recognized inside their functions, variables with the same name can be used in different functions.

Local variables are created when a function starts, and deleted when the function is completed.

## Function Scope

JavaScript has function scope: Each function creates a new scope.

Variables defined inside a function are not accessible (visible) from outside the function.

Variables declared with `var`, `let` and `const` are quite similar when declared inside a function.

They all have **Function Scope**:

```js
function myFunction() {  
  var carName = "Volvo";   // Function Scope  let const 
}
```

## Global JavaScript Variables

A variable declared outside a function, becomes **GLOBAL**.

```js
let carName = "Volvo";  
// code here can use carName  
  
function myFunction() {  
// code here can also use carName  
}
```

## Global Scope

Variables declared **Globally** (outside any function) have **Global Scope**.

**Global** variables can be accessed from anywhere in a JavaScript program.

Variables declared with `var`, `let` and `const` are quite similar when declared outside a block.

They all have **Global Scope**

## Automatically Global

If you assign a value to a variable that has not been declared, it will automatically become a **GLOBAL** variable.

This code example will declare a global variable `carName`, even if the value is assigned inside a function.


```js
myFunction();  
  
// code here can use carName  
  
function myFunction() {  
  carName = "Volvo";  
}
```

