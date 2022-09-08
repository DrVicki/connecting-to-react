# Front-End Integration

## Connecting to React

Since this course is on .NET Core and not React, this section is going to rely on your previous React experience and will not be going into detail about the steps. All necessary code will be here to test it out even without previous knowledge of React. If you plan on using Angular exclusively, skip to the next section.

If you've previously installed `create-react-app` globally via `npm install -g create-react-app`, we recommend you uninstall the package using `npm uninstall -g create-react-app` or `yarn global remove create-react-app` to ensure that npx always uses the latest version.

### Create React App

1. Open the terminal, navigate to your course folder and then run the `npx-create-react-app` command with the project name of `react-api-eater`.

```
cd desktop
cd Programming/CSharp
npx create-react-app react-api-eater
cd react-api-eater
```

To run the app open the VS Code built-in terminal and enter `npm start`. The browser will greet you on the default home page.

Then open http://localhost:3000/ to see your app.

![](https://github.com/DrVicki/connecting-to-react/blob/main/images2/react.png)

When you’re ready to deploy to production, create a minified bundle with `npm run build`.

### Creating an App

You’ll need to have Node >= 14 on your local development machine (but it’s not required on the server). You can use nvm (macOS/Linux) or nvm-windows to switch Node versions between different projects.

To create a new app:
    - `npx create-react-app my-app`

#### Selecting a package manager

When you create a new app, the CLI will use npm or Yarn to install dependencies, depending on which tool you use to run `create-react-app`. For example:

```
# Run this to use npm
npx create-react-app my-app
# Or run this to use yarn
yarn create react-app my-app
```

#### Output

Running any of these commands will create a directory called `my-app` inside the current folder. Inside that directory, it will generate the initial project structure and install the transitive dependencies:

![](https://github.com/DrVicki/connecting-to-react/blob/main/images2/folderstructure.png)

No configuration or complicated folder structures, only the files you need to build your app. Once the installation is done, you can open your project folder:

`cd react-api-eater`

### Scripts

Inside the newly created project, you can run some built-in commands:

`npm start` or `yarn start`

Runs the app in development mode. Open http://localhost:3000 to view it in the browser.

    - The page will automatically reload if you make changes to the code. You will see the build errors and lint warnings in the console.
    
`npm run build` or `yarn build`

Builds the app for production to the build folder. It correctly bundles React in production mode and optimizes the build for the best performance.

    - The build is minified and the filenames include the hashes.

    - Your app is ready to be deployed.

## Add a Component

Defining a component can seem tricky until you have some practice, but the gist is:

    - If it represents an obvious "chunk" of your app, it's probably a component
    - If it gets reused often, it's probably a component.

That second bullet is especially valuable: making a component out of common UI elements allows you to change your code in one place and see those changes everywhere that component is used. 
    - You don't have to break everything out into components right away, either. Let's take the second bullet point as inspiration and make a component out of the most reused, most important piece of the UI: a todo list item.
    
## Make a <Todo />

Before we can make a component, we should create a new file for it. In fact, we should make a directory just for our components. The following commands make a components directory and then, within that, a file called `Todo.js`. Make sure you're in the root of your app before you run these!

```
mkdir src/components
touch src/components/Todo.js
```

Our new `Todo.js` file is currently empty! Open it up and give it its first line:

`import React from "react"`;

Since we're going to make a component called `Todo`, you can start adding the code for that to `Todo.js` too, as follows. In this code, we define the function and export it on the same line:

```
export default function Todo() {
  return (
    // …
  );
}
```

This is OK so far, but our component has to return something! Go back to src/App.js, copy the first <li> from inside the unordered list, and paste it into Todo.js so that it reads like this:

export default function Todo() {
  return (
    <li className="todo stack-small">
      <div className="c-cb">
        <input id="todo-0" type="checkbox" defaultChecked={true} />
        <label className="todo-label" htmlFor="todo-0">
          Eat
        </label>
      </div>
      <div className="btn-group">
        <button type="button" className="btn">
          Edit <span className="visually-hidden">Eat</span>
        </button>
        <button type="button" className="btn btn__danger">
          Delete <span className="visually-hidden">Eat</span>
        </button>
      </div>
    </li>
  );
}
Copy to Clipboard
Note: Components must always return something. If at any point in the future you try to render a component that does not return anything, React will display an error in your browser.

Our Todo component is complete, at least for now; now we can use it. In App.js, add the following line near the top of the file to import Todo:

import Todo from "./components/Todo";
Copy to Clipboard
With this component imported, you can replace all of the <li> elements in App.js with <Todo /> component calls. Your <ul> should read like this:

<ul
  role="list"
  className="todo-list stack-large stack-exception"
  aria-labelledby="list-heading"
>
  <Todo />
  <Todo />
  <Todo />
</ul>
Copy to Clipboard
When you look back at your browser, you'll notice something unfortunate: your list now repeats the first task three times!










