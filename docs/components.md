# Basic Components

1. A component in ReactJS can be declared like a javascript function but has to be exported as a module:

```javascript
// File: MyComponent.js

export default MyComponent = () => {
    return (
        <div>
            Content
        </div>
    )
}
```

Like functions, it has to have a return value which should always be a single `html` element.

2. A component is called or rendered in another component by treating it as an `html` element.

```javascript
// File: App.js
import MyComponent from "./MyComponent";

export default App = () => {
    return (
        <div>
            <h1>My Application</h1>
            <MyComponent/>
        </div>
    )
}
```

3. We can also have functions within a component that renders stuff.

```js
export default MyComponent = () => {
    const renderContent = () => {
        return (
            <h1>
                Content
            </h1>
        )
    }

    return (
        <div>
            {renderContent()}
        </div>
    )
}
```

Notice how we embed javascript within the `html` being returned by using the `{}` symbols.

4. Variables also work the same way as well as interpolating them within content:

```js
export default MyComponent = () => {
    const renderContent = (content) => {
        return (
            <h1>
                {`${content}`}
            </h1>
        )
    }

    return (
        <div>
            {renderContent('Hello World')}
        </div>
    )
}
```
