### 1. if / else

Used for full control flow, usually outside JSX.

###### Example:
```
function Status({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  } else {
    return <h1>Please login</h1>;
  }
}
```
###### Key points:
- Cannot be used directly inside JSX
- Best for complex conditions or multiple returns
- Very readable
### 2. Ternary Operator (condition ? A : B)

Used inside JSX for inline conditions.

###### Example:
```
function Status({ isLoggedIn }) {
  return (
    <h1>
      {isLoggedIn ? "Welcome back!" : "Please login"}
    </h1>
  );
}
```
### Key points:
- Short and concise
- Must provide both true and false cases
- Can get messy if nested

### 3. Logical AND (&&)

Used when you want to render something only if condition is true.

###### Example:
```
function Notification({ hasMessage }) {
  return (
    <div>
      {hasMessage && <p>You have a new message!</p>}
    </div>
  );
}
```
###### Key points:
- No else part
- If condition is false → nothing renders
- Very clean for simple checks