## Arrow Functions

Arrow functions allow us to write shorter function syntax:

### Before:
```jsx
hello = function() {
  return "Hello World!";
}
```

### With Arrow Function:
```jsx
hello = () => {
  return "Hello World!";
}
```

It gets shorter! If the function has only one statement, and the statement returns a value, you can remove the brackets _and_ the `return` keyword:

### Arrow Functions Return Value by Default:

```jsx
hello = () => "Hello World!";
```

**Note:** This works only if the function has only one statement.

If you have parameters, you pass them inside the parentheses:

### Arrow Function With Parameters:

```jsx
hello = (val) => "Hello " + val;
```

In fact, if you have only one parameter, you can skip the parentheses as well:

### Arrow Function Without Parentheses:

```jsx
hello = val => "Hello " + val;
```

## What About `this`?

The handling of `this` is also different in arrow functions compared to regular functions.

In short, with arrow functions there is no binding of `this`.

In regular functions the `this` keyword represented the object that called the function, which could be the window, the document, a button or whatever.

With arrow functions, the `this` keyword _always_ represents the object that defined the arrow function.

Let us take a look at two examples to understand the difference.

Both examples call a method twice, first when the page loads, and once again when the user clicks a button.

The first example uses a regular function, and the second example uses an arrow function.

The result shows that the first example returns two different objects (window and button), and the second example returns the Header object twice.

### Example

With a regular function, `this` represents the object that called the function:

```jsx
class Header {
  constructor() {
    this.color = "Red";
  }

//Regular function:
  changeColor = function() {
    document.getElementById("demo").innerHTML += this;
  }
}

const myheader = new Header();

//The window object calls the function:
window.addEventListener("load", myheader.changeColor);

//A button object calls the function:
document.getElementById("btn").addEventListener("click", myheader.changeColor);
```

### Example

With an arrow function, `this` represents the Header object no matter who called the function:

```jsx
class Header {
  constructor() {
    this.color = "Red";
  }

//Arrow function:
  changeColor = () => {
    document.getElementById("demo").innerHTML += this;
  }
}

const myheader = new Header();


//The window object calls the function:
window.addEventListener("load", myheader.changeColor);

//A button object calls the function:
document.getElementById("btn").addEventListener("click", myheader.changeColor);
```

Remember these differences when you are working with functions. Sometimes the behavior of regular functions is what you want, if not, use arrow functions.