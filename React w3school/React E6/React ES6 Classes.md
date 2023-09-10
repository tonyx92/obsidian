
## Classes

ES6 introduced classes.

A class is a type of function, but instead of using the keyword `function` to initiate it, we use the keyword `class`, and the properties are assigned inside a `constructor()` method.

```jsx
class Car {
  constructor(name) {
    this.brand = name;
  }
}
```

Create an object called "mycar" based on the Car class:

```jsx
class Car {
  constructor(name) {
    this.brand = name;
  }
}

const mycar = new Car("Ford");
```

## Method in Classes

You can add your own methods in a class:

### Example

Create a method named "present":
```jsx
class Car {
  constructor(name) {
    this.brand = name;
  }
  
  present() {
    return 'I have a ' + this.brand;
  }
}

const mycar = new Car("Ford");
mycar.present();
```

As you can see in the example above, you call the method by referring to the object's method name followed by parentheses (parameters would go inside the parentheses).

## Class Inheritance

To create a class inheritance, use the `extends` keyword.

A class created with a class inheritance inherits all the methods from another class:

### Example

Create a class named "Model" which will inherit the methods from the "Car" class:

```jsx
class Car {
  constructor(name) {
    this.brand = name;
  }

  present() {
    return 'I have a ' + this.brand;
  }
}

class Model extends Car {
  constructor(name, mod) {
    super(name);
    this.model = mod;
  }  
  show() {
      return this.present() + ', it is a ' + this.model
  }
}
const mycar = new Model("Ford", "Mustang");
mycar.show();
```

The `super()` method refers to the parent class.

By calling the `super()` method in the constructor method, we call the parent's constructor method and get access to the parent's properties and methods.

To learn more about classes, check out our [JavaScript Classes](https://www.w3schools.com/js/js_class_intro.asp) section.
