# Bootstrapping a Project

1. Initialize a NodeJS project

```bash
npm init
```

2. Create a `public` directory inside the project with the following content:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>
      My ReactJS Application
    </title>
    <script src="./assets/index.js" async defer></script>
    <link rel="stylesheet" href="./assets/styles/index.css">
  </head>
  <body id="bootstrap-overrides">
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
  </body>
</html>
```

Notice that it is referencing a file called `index.js` in an `assets` folder for javascript and an `index.css` file inside the folder `assets/styles`. Since we don't have those folders (not files) yet, let's create those folders. You should now have the following inside `public`:

```
public
    |
    |---assets/styles
```

3. Create a `src` directory to hold all source code for the ReactJS project with an entry point file called `index.js`. Content of `index.js` should look like:

```js
import React from 'react';
import App from './js/App';

const container = document.getElementById("root");
const root = ReactDOM.createRoot(container);

root.render(
  <App/>
);
```

Notice how it's taking some html element called `root` and mounting your first React component in it called `App`.

4. Since `App` doesn't exist yet, let's create it iniside `src/js/App.js`:

```js
import React from "react";

export default App = () => {
    return (
        <div>
            My ReactJS Application
        </div>
    )
}
```

5. To make sure we have an entry point for our css, create a file called `index.scss` in `src/styles/index.scss` (empty is ok for now)

6. Download the `build.js` builder file and put it in the root of your project. Notice how `entryPoints` configuration points to both `index.js` and `index.scss`. Notice how `outdir` points to `public/assets`.

7. Install common dependencies needed including the `react` library:

```bash
npm install \
    autoprefixer \
    axios \
    bcrypt \
    bootstrap \
    cors \
    dotenv \
    esbuild \
    esbuild-sass-plugin \
    esbuild-envfile-plugin \
    express \
    jsonwebtoken \
    jwt-decode \
    react \
    react-bootstrap \
    react-dom \
    react-router-dom
```

On Windows:

```bash
npm install autoprefixer axios bcrypt bootstrap cors dotenv esbuild esbuild-sass-plugin esbuild-envfile-plugin express jsonwebtoken jwt-decode react react-bootstrap react-dom react-router-dom
```

8. Create a `.env` file to hold environment variables needed in the build process:

```
API_BASE_URL=http://localhost:3000
TOKEN_BEARER=MY_USER
CURRENT_USER=MY_USER
```

9. Run and compile the application:

Change `type` in `package.json` to value `module`

Raw command:

```bash
node build.js --dev --watch
```

Modify `package.json` to include a script called `"start"`

```js
// Inside package.json scripts
"start": "node build.js --dev --watch"
```

To run:

```bash
npm run start
```

10. Visit the application from your browser in `http://localhost:8000`
