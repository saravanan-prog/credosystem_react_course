## React Lists


In React, rendering lists and using keys properly is fundamental for building dynamic UIs.

### 🔹 Rendering Lists using map()

- You use JavaScript’s map() to transform an array into JSX elements.
- map() loops through the array and returns a `<li>` for each item.

###### Example:
```
function FruitList() {
  const fruits = ["Apple", "Banana", "Mango"];

  return (
    <ul>
      {fruits.map((fruit) => (
        <li>{fruit}</li>
      ))}
    </ul>
  );
}
```


###### ⚠️ Problem: Missing Keys

- If you run the above code, React will warn:
- “Each child in a list should have a unique ‘key’ prop”

###### 🔹 Importance of Keys

- A key is a unique identifier for each element in a list.

### Correct Example:
```
function FruitList() {
  const fruits = ["Apple", "Banana", "Mango"];

  return (
    <ul>
      {fruits.map((fruit, index) => (
        <li key={index}>{fruit}</li>
      ))}
    </ul>
  );
}
```
### 🔑 Why Keys Matter

React uses keys for its reconciliation process (diffing algorithm):

- Identify which items changed
- Update only what’s necessary
- Improve performance
- Prevent UI bugs

### ⚡ Real Example (Dynamic Data)
```
function Users({ users }) {
  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```
👉 Best practice: use a unique ID from data, not index.

### ❌ Why NOT Always Use Index as Key?

Using index can cause bugs when:

- Items are reordered
- Items are added/removed

👉 React may reuse wrong elements → UI issues