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
    
![](https://github.com/DrVicki/connecting-to-react/blob/main/images2/react.png)
    
`npm run build` or `yarn build`

Builds the app for production to the build folder. It correctly bundles React in production mode and optimizes the build for the best performance.

    - The build is minified and the filenames include the hashes.

    - Your app is ready to be deployed.

**Install the dependencies required in this project by typing the given command in the terminal.*

```
npm install react-router-dom 
npm install --save styled-components
```

## Add Components

Defining a component can seem tricky until you have some practice, but the gist is:

    - If it represents an obvious "chunk" of your app, it's probably a component
    - If it gets reused often, it's probably a component.


Now create the `Components` folder in `src` then go to the `Components` folder and create a new folder name `Navbar`.In `Navbar` folder create two files `Navbar.js` and `NavbarElements.js`. Create one more folder in `src` named `pages` and in `pages` create files name `about.js`, `blogs.js`, `index.js`.

```
mkdir src/Components
mkdir src/Components/Navbar
touch src/Components/Navbar/Navbar.js
touch src/Components/Navbar/NavbarElements.js
mkdir src/Components/pages
touch src/Components/pages/about.js
touch src/Components/pages/blogs.js
touch src/Components/pages/index.js
```


### Create the navbar and style it.

Navbar.js

```
import React from "react";
import { Nav, NavLink, NavMenu }
	from "./NavbarElements";

const Navbar = () => {
return (
	<>
	<Nav>
		<NavMenu>
		<NavLink to="/about" activeStyle>
			About
		</NavLink>
		<NavLink to="/blogs" activeStyle>
			Blogs
		</NavLink>
		</NavMenu>
	</Nav>
	</>
);
};

export default Navbar;
```

NavbarElements.js

```
import { FaBars } from "react-icons/fa";
import { NavLink as Link } from "react-router-dom";
import styled from "styled-components";

export const Nav = styled.nav`
background: #ffb3ff;
height: 85px;
display: flex;
justify-content: space-between;
padding: 0.2rem calc((100vw - 1000px) / 2);
z-index: 12;
`;

export const NavLink = styled(Link)`
color: #808080;
display: flex;
align-items: center;
text-decoration: none;
padding: 0 1rem;
height: 100%;
cursor: pointer;
&.active {
	color: #4d4dff;
}
`;

export const Bars = styled(FaBars)`
display: none;
color: #808080;
@media screen and (max-width: 768px) {
	display: block;
	position: absolute;
	top: 0;
	right: 0;
	transform: translate(-100%, 75%);
	font-size: 1.8rem;
	cursor: pointer;
}
`;

export const NavMenu = styled.div`
display: flex;
align-items: center;
margin-right: -24px;
/* Second Nav */
/* margin-right: 24px; */
/* Third Nav */
/* width: 100vw;
white-space: nowrap; */
@media screen and (max-width: 768px) {
	display: none;
}
`;
```

### Edit pages in the project in `src/pages`

src/pages/about.js

```
import React from "react";

const About = () => {
return (
	<div>
	<h1>
		LearningSource creates Software Developers!
	</h1>
	</div>
);
};

export default About;
```

src/pages/blogs.js

```
import React from 'react';

const Blogs = () => {
return (
	<h1>You can write your blogs!</h1>
);
};

export default Blogs;
```

src/pages/index.js

```
import React from 'react';

const Home = () => {
return (
	<div>
	<h1>Welcome to LearningSource</h1>
	</div>
);
};

export default Home;
```

index.js

```
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```

app.js

```
/* eslint-disable react/jsx-no-duplicate-props */
/* eslint-disable no-unused-vars */

import React from 'react';
import './App.css';
import Navbar from './Components/NavBar/Navbar';
import { BrowserRouter as Router, Routes, Route}
	from 'react-router-dom';

import About from './pages/about';
import Blogs from './pages/blogs';


function App() {
return (
	<Router>
	<Navbar />
	<Routes>
		<Route path='/about' element={<About/>} />
		<Route path='/blogs' element={<Blogs/>} />
		
	</Routes>
	</Router>
);
}

export default App;
```

## Run the Application

Now to run the above code open the terminal and type the following command.

`npm start`

![](https://github.com/DrVicki/connecting-to-react/blob/main/images2/run.png)
![]
