Just like HTML DOM events, React can perform actions based on user events.

React has the same events as HTML: click, change, mouseover etc.

---

## Adding Events

React events are written in camelCase syntax:

`onClick` instead of `onclick`.

React event handlers are written inside curly braces:

`onClick={shoot}`  instead of `onClick="shoot()"`.

### React:

```jsx
<button onClick={shoot}>Take the Shot!</button>
```

### HTML:

```html
<button onclick="shoot()">Take the Shot!</button>
```

  

### Example:

Put the `shoot` function inside the `Football` component:

```jsx
function Football() {
  const shoot = () => {
    alert("Great Shot!");
  }

  return (
    <button onClick={shoot}>Take the shot!</button>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Football />);
```

[Run Example »](https://www.w3schools.com/react/showreact.asp?filename=demo2_react_events_handler)

## Passing Arguments

To pass an argument to an event handler, use an arrow function.

### Example:

Send "Goal!" as a parameter to the `shoot` function, using arrow function:

```jsx
function Football() {
  const shoot = (a) => {
    alert(a);
  }

  return (
    <button onClick={() => shoot("Goal!")}>Take the shot!</button>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Football />);
```

[Run Example »](https://www.w3schools.com/react/showreact.asp?filename=demo2_react_events_argument)

---

## React Event Object

Event handlers have access to the React event that triggered the function.

In our example the event is the "click" event.

### Example:

Arrow Function: Sending the event object manually:

```jsx
function Football() {
  const shoot = (a, b) => {
    alert(b.type);
    /*
    'b' represents the React event that triggered the function,
    in this case the 'click' event
    */
  }

  return (
    <button onClick={(event) => shoot("Goal!", event)}>Take the shot!</button>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Football />);
 
```

[Run Example »](https://www.w3schools.com/react/showreact.asp?filename=demo2_react_events_event)

This will come in handy when we look at [Form](https://www.w3schools.com/react/react_forms.asp) in a later chapter.