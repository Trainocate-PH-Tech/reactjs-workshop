# State Management

## Declaring States

A state will have a variable and a setter for that variable. It is initialized by the `React.useState()` function where you can pass in a default value.

```js
// Inside your component

// A state called message with a default value ""
const [message, setMessage] = React.useState("");
```

Whenever some logic modifies the state, all parts of the application using that state will get the new value. **The only wat to modify a state is to call its setter method**.

### Example: Modifying `message` with UI

Here we bind the `message` state to the value of the input. Every time the user triggers `onChange` by typing something in the input box, a function is called which sets the new value of message using `setMessage`. As a result, all parts of the application using `message` will get the updated value.

```js
<input 
    value={message}
    onChange={(event) => {
        setMessage(event.target.value);
    }}
/>
```

In short, a component will be "refreshed" if the value of a state is updated.

## Working with Objects

States can also be complex data types like arrays or lists which are considered objects.

```js
// A state with an empty array as a default value
const [items, setItems] = React.useState([]);
```

Whenever we update an object, the practice is to first create a copy of an object.

```js
// Create a copy of the object items using ... and pushing in a new value
setItems([...items, newValue]);
```

```js
// Alternatively, we can also push a new value into the copy of the array
setItems([...].push(newValue));
```

When working wiht lists and rendering components from each item of the list, we need to provide a `key` attribute to each element that is rendered. A `key` should be unique althroughout the component.

**Example: Creating a List of Items**

```js
{items.map((item, i) => {
    return (
        <li key={`item-${i}`}>
            {item}
        </li>
    )
})}
```
