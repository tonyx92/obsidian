## Ternary Operator

The ternary operator is a simplified conditional operator like `if` / `else`.

Syntax: `condition ? <expression if true> : <expression if false>`

Here is an example using `if` / `else`:

### Before:

```jsx
if (authenticated) {
  renderApp();
} else {
  renderLogin();
}
```

[Try it Yourself »](https://www.w3schools.com/react/tryit.asp?filename=tryreact_es6_ternary1)

Here is the same example using a ternary operator:

### With Ternary

```jsx
authenticated ? renderApp() : renderLogin();
```

[Try it Yourself »](https://www.w3schools.com/react/tryit.asp?filename=tryreact_es6_ternary2)
