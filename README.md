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

### Add a Component

Inside the `src` folder add a new folder and name it `Components` then add a file named `Values.js` to the folder. Inside the `Values.js` file add the following code to create the Value component. This component returns a single div with the values from the back.

```
import React from 'react';

class Values extends React.Component {
    state = {
        values: []
    };

    callValues = () => {
        fetch('http://localhost:5000/api/values')
            .then(response => response.json())
            .then(data => {
                console.log('callValues: ', data);
                this.setState(() => {
                    return {
                        values: data
                    };
                });
                console.log('after SetState: ', this.state.values);
            });
    };

    componentDidMount() {
        this.callValues();
        console.log('componentDidMount: ', this.state.values);
    }

    render() {
        return <div>{this.state.values}</div>;
    }
}

export default Values;
```

### Render the Component

Navigate to `src > App.js` and import the Values component you just created. Then add the component to the App classes render method. The `App.js` file should look like below:


```
import React, { Component } from 'react';
import './App.css';
import Values from './Components/Values';

class App extends Component {
    render() {
        return (
        <div className="App">
            <h1 className="App-title">Welcome to React</h1>
            <Values />
        </div>
        );
    }
}

export default App;
```












