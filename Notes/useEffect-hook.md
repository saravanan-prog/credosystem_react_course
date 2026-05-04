## useEffect Hook (in React)
```
useEffect is used to handle side effects in functional components.
```
### 🔹 What are Side Effects?
```
Side effects are operations that happen outside of rendering UI.
```
### Examples:
- API calls
- Timers (setTimeout, setInterval)
- Event listeners
- DOM updates (e.g., document.title)

👉 React components should be pure → side effects go inside useEffect

### 🔹 Syntax
```
useEffect(() => {
  // side effect code

  return () => {
    // cleanup function (optional)
  };
}, [dependencies]);
```
###### 🔹 API Calls Example
```
import { useEffect, useState } from "react";

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(res => res.json())
      .then(data => setUsers(data));
  }, []);

  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```
👉 Runs once when component mounts

### Dependency Array
```
Controls when the effect runs
```
##### Cases: No dependency array

```
useEffect(() => {
  console.log("Runs every render");
});
```


##### Empty array []
```       
    useEffect(() => {
        console.log("Runs only once");
    }, []);

```
##### With dependencies
```       
useEffect(() => {
  console.log("Runs when count changes");
}, [count]);
```
### Cleanup Function

 Used to clean up side effects to avoid memory leaks.

#### Example: Timer cleanup
```
useEffect(() => {
  const timer = setInterval(() => {
    console.log("Running...");
  }, 1000);

  return () => {
    clearInterval(timer);
  };
}, []);
```

#### Example: Event listener cleanup
```
useEffect(() => {
  const handleResize = () => console.log(window.innerWidth);
   window.addEventListener("resize", handleResize);
  return () => {
    window.removeEventListener("resize", handleResize);
  };
}, []);
```
#### 🔹 Key Points
- Runs after render
- Handles side effects
- Dependency array controls execution
- Cleanup prevents memory leaks