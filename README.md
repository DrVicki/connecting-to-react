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


No configuration or complicated folder structures, only the files you need to build your app. Once the installation is done, you can open your project folder:

`cd react-api-eater`

### Add a Component








