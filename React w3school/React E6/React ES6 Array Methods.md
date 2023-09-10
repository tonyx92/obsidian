## Array Methods

There are many JavaScript array methods.

One of the most useful in React is the `.map()` array method.

The `.map()` method allows you to run a function on each item in the array, returning a new array as the result.

In React, `map()` can be used to generate lists.

### Example

Generate a list of items from an array:

```jsx
const myArray = ['apple', 'banana', 'orange'];

const myList = myArray.map((item) => <p>{item}</p>) 
```