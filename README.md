# React Crash Course

Traversy Media
<https://www.youtube.com/watch?v=w7ejDZ8SWv8>

## React

- React is a library for building user interfaces
- React runs on the client as a SPA (Single Page APP)
- React can be used to build full stack apps by communicating with a server/API (eg. MERN stack)
- React is often reffered as a front-end "framework" because it is capable and directly comparable to a framework such as Angular or Vue

## Why use React ?

- Structure the "view" layer of your application
- Reusable components with their own state
- JSX (JavaScript Syntax Extension) - Dynamic markup
- Interactive UIs with Virtual DOM
- Performance & testing
- Very popular in the industry

## Learn JavaScript

- Data types, variables, functions, loops, etc
- Promises & asynchronus programming
- Array methods like forEach() & map()
- Fetch API & making HTTP requests

## Task Tracker APP

- When using React, think of your UI as a bunch of separate components
![ui-components-task-tracker-app](readme-images\ui-components-task-tracker-app.png)

## Components: Functions vs. Classes

### Function component

```jsx
export const Header = () => {
    return (
        <div>
            <h1>My Header</h1>
        </div>
    )
}
```

### Class component

```jsx
export default class Header extends React.Component {
    render() {
        return() {
            <div>
                <h1>My Header</h1>
            </div>
        }
    }
}
```

- Components render/return JSX (JavaScript Syntax Extension)
- Components can also take in "props"

    ```html
    <Header title="My Title" />
    ```

## Workig with State

- Components can have "state" which is an object that determines how a component renders and behaves
- "App" or "global" state refers to state that is available to the entire UI, not just a single component.
- Prior to React 16.8, we had to use class based components to use state.
- Now we can use functional components with __hooks__

## React Hooks

__React Hooks__ are functions that let us __hook__ into the __React__ state and lifecycle features from function components

- __useState__ - Returns a stateful value and a function to update it
- __useEffect__ - Performs side effects in function components
- __useContext, useReducer, useRef__, - Beyond the scope of this course

You can also create your own custom hooks

## Let's Learn React

### Create react app

<https://reactjs.org/docs/create-a-new-react-app.html#create-react-app>

- Requires Node.js <https://nodejs.org/en/>
- Install React Developer Tools [chorme extension](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)
- Check npm version (must be >= 5.6)

    ```bash
    npm --version
    ```

- Create a new react app

    ```bash
    npx create-react-app react-task-tracker
    cd react-task-tracker
    code .
    ```

- `package.json` has all the dependencies that are included
- `npm start` to start up the dev server
- `index.html` inside `public` folder is single page of SPA that is being loaded
- `index.js` inside `src` folder is the entry point for the react app
  - `<App />` is the root component with code inside `App.js`
  - When returning `JSX` you can only return single parent element

## Create Components

- Create a `components` folder inside the `src` folder
- Create __Header__ component
  - `Header.js` file inside components folder
  - Install a VSCode extension __ES7 React/Redux/GraphQL/React-Native snippets__
    - `rcc` - create class based components
    - `rce` - create class based component and export
    - `rafce` - creates an arrow function and exports it (very clean)
  - inside `Header.js` type `rafce` and press `TAB` to create boiler place of arrow function component

    ```jsx
    import React from 'react'

        const Header = () => {
            return (
                <div>
                    
                </div>
            )
        }

        export default Header

    ```

  - `import React from 'react'` this is no logner required so we can get rid of that
  
  - Your final __Header__ component `Header.js`

    ```jsx
    const Header = () => {
        return (
            <header>
                <h1>Task Tracker</h1>
            </header>
        )
    }

    export default Header
    ```

  - import your __Header__ component in `App.js` and embed it like an XML tag

    - Function based component

        ```jsx
        import Header from './components/Header'

        function App() {
        return (
            <div className="contianer">
            <Header />
            </div>
        );
        }

        export default App;
        ```

    - Class based component

        ```jsx
        import React from 'react'
        import Header from './components/Header'

        class App extends React.Component {
            render(){
                return <h1>Hello from a class</h1>
            }
        }
        export default App;
        ```

  - __Props__ we can recive props inside our components

    ```jsx
    <Header title='Header Title' />
    ```

    ```jsx
    const Header = (props) => {
        return (
            <header>
                <h1>{props.title}</h1>
            </header>
        )
    }

    Header.defaultProps = {
        title: 'Task Tracker',
    }
    export default Header
    ```

  - Destructre `props` object

    ```jsx
    const Header = ({ title }) => {
        return (
            <header>
                <h1>{title}</h1>
            </header>
        )
    }

    Header.defaultProps = {
        title: 'Task Tracker',
    }
    export default Header
    ```

  - __PropTypes__ is built in type system for your properties
    - `impt` - to import __PropTypes__
    - final __Header__ component with __PropTypes__

        ```jsx
        import PropTypes from 'prop-types'

        const Header = ({ title }) => {
            return (
                <header>
                    <h1>{title}</h1>
                </header>
            )
        }

        Header.defaultProps = {
            title: 'Task Tracker',
        }

        Header.propTypes = {
            title: PropTypes.string.isRequired,
        }

        export default Header
        ```

        here we have specified that type of `title` is `string` if we pass a variable of type `number` we will get a warning in the browser console. This helps in writing robust code and catch errors. We can also use __TypeScript__ with React.

## Styling

- You can use `index.css` inside `src` folder
  - For this project we will use index.css, you can copy the code from here :

    <https://github.com/bradtraversy/react-crash-2021/blob/master/src/index.css>

- You can also use style components which is external package and is very popular
- You can also use direct css in javascript
  
  ```jsx
  <h1 style={{color: 'red', backgroundColor: 'black'}}>{title}</h1>
  ```

  This can also be done by specifying a constant as below

  ```jsx
  import PropTypes from 'prop-types'

    const Header = ({ title }) => {
        return (
            <header>
                <h1 style={headingStyle}>{title}</h1>
            </header>
        )
    }

    Header.defaultProps = {
        title: 'Task Tracker',
    }

    Header.propTypes = {
        title: PropTypes.string.isRequired,
    }

    // CSS in JS
    const headingStyle = {
        color: 'red', 
        backgroundColor: 'black'
    }

    export default Header
    ```

## Add a button

- directly as html element

```jsx
import PropTypes from 'prop-types'

const Header = ({ title }) => {
    return (
        <header className="header">
            <h1>{title}</h1>
            <button className='btn'>Add</button>
        </header>
    )
}

Header.defaultProps = {
    title: 'Task Tracker',
}

Header.propTypes = {
    title: PropTypes.string.isRequired,
}

// CSS in JS
// const headingStyle = {
//     color: 'red', 
//     backgroundColor: 'black'
// }

export default Header
```

- Create a button as a Component
  - inside `components` folder create a new file `Button.js`
- type `rafce` and press `TAB` to generate boiler plate for your button component
- final `Button.js` component

```jsx
import PropTypes from 'prop-types'

const Button = ({color, text}) => {
    return <button style={{ backgroundColor: color}} className='btn'>{text}</button>
}

Button.defaultProps = {
    color: 'steelblue'
}

Button.propTypes = {
    text: PropTypes.string,
    color: PropTypes.string,
}

export default Button
```

- import button component inside `Header.js` component

```jsx
import PropTypes from 'prop-types'
import Button from './Button'

const Header = ({ title }) => {
    return (
        <header className="header">
            <h1>{title}</h1>
            <Button color='green' text='Add' />
        </header>
    )
}

Header.defaultProps = {
    title: 'Task Tracker',
}

Header.propTypes = {
    title: PropTypes.string.isRequired,
}

export default Header
```

- We can reuse button component as many times as we want and create many buttons with different props (colors and text)

```jsx
const Header = ({ title }) => {
    return (
        <header className="header">
            <h1>{title}</h1>
            <Button color='green' text='Hello' />
            <Button color='blue' text='Hello Blue' />
            <Button color='red' text='Hello Red' />
        </header>
    )
}
```

## Events

- add an __event__ in your __button__ in `Button.js` component

```jsx
import PropTypes from 'prop-types'

const Button = ({color, text}) => {

    const onClick = (e) => {
        // log the click event e
        console.log(e) 
    }
    return (
        <button onClick={onClick} style={{ backgroundColor: color}} 
        className='btn'>
            {text}
        </button>
    )
}

Button.defaultProps = {
    color: 'steelblue'
}

Button.propTypes = {
    text: PropTypes.string,
    color: PropTypes.string,
}

export default Button
```

- we can also pass onClick function as as a `prop` from `Header.js` component

    Header.js

    ```jsx
    const Header = ({ title }) => {
        const onClick = () => {
            console.log('Click')
        }

        return (
            <header className="header">
                <h1>{title}</h1>
                <Button color='green' text='Add' onClick={onClick} />
            </header>
        )
    }
    ```

    Button.js

    ```jsx
    import PropTypes from 'prop-types'

    const Button = ({color, text, onClick}) => {
        return (
            <button onClick={onClick} style={{ backgroundColor: color}} 
            className='btn'>
                {text}
            </button>
        )
    }

    Button.defaultProps = {
        color: 'steelblue'
    }

    Button.propTypes = {
        text: PropTypes.string,
        color: PropTypes.string,
        onClick: PropTypes.func,
    }

    export default Button
    ```

## Tasks Component

- Create a new file `Tasks.js` Tasks component in `components` folder
- Map through tasks and output in HTML, by creating list and we can create list by using `map()` array method

    ```jsx
    const tasks = [
    {
        id: 1,
        text: "Doctors Appointment",
        day: "Feb 5th at 2:30pm",
        reminder: true,
    },
    {
        id: 2,
        text: "Meeting at School",
        day: "Feb 6th at 1:30pm",
        reminder: true,
    },
    {
        id: 3,
        text: "Food Shopping",
        day: "Feb 5th at 2:30pm",
        reminder: false,
    },
    ];

    const Tasks = () => {
    return (
        <>
        {tasks.map((task) => (
            <h3 key={task.id}>{task.text}</h3>
        ))}
        </>
    );
    };

    export default Tasks;
    ```

- import `Tasks.js` component in `App.js` root component

    ```jsx
    import Header from './components/Header'
    import Tasks from './components/Tasks'

    function App() {
    return (
        <div className="contianer">
        <Header />
        <Tasks />
        </div>
    );
    }

    export default App;

    ```

## State & useState Hook

- Define `tasks` as part of our component `state`.

    ```jsx
    import {useState} from 'react'

    const Tasks = () => {
    const [tasks, setTasks] = useState([
        {
            id: 1,
            text: "Doctors Appointment",
            day: "Feb 5th at 2:30pm",
            reminder: true,
        },
        {
            id: 2,
            text: "Meeting at School",
            day: "Feb 6th at 1:30pm",
            reminder: true,
        },
        {
            id: 3,
            text: "Food Shopping",
            day: "Feb 5th at 2:30pm",
            reminder: false,
        },
    ])
    return (
        <>
        {tasks.map((task) => (
            <h3 key={task.id}>{task.text}</h3>
        ))}
        </>
    );
    };

    export default Tasks;
    ```

- To change any task of the `state` we use `setTasks`
- Note: We would not do `tasks.push()` to add because state is immutable. we cannot directly change state we basically recreate it and pass it thorugh. Its one way data. we ca do following to add tasks

    ```jsx
    return (
        setTasks([...tasks, {}])
        <>
        {tasks.map((task) => (
            <h3 key={task.id}>{task.text}</h3>
        ))}
        </>
    );
    ```

- We donot want tasks defined inside task component, we would want to access tasks from other components. We can use `contextapi` or `redux`

- For now we will put tasks inside `App.js` as __global state__, then we can pass it down to components as `props`.

## Global State

- State should be at the top level, so that we can use state in other components

`App.js` component

```jsx
import {useState} from 'react'
import Header from './components/Header'
import Tasks from './components/Tasks'

function App() {
  const [tasks, setTasks] = useState([
    {
        id: 1,
        text: "Doctors Appointment",
        day: "Feb 5th at 2:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Meeting at School",
        day: "Feb 6th at 1:30pm",
        reminder: true,
      },
      {
        id: 3,
        text: "Food Shopping",
        day: "Feb 5th at 2:30pm",
        reminder: false,
      },
  ])
  return (
    <div className="contianer">
      <Header />
      <Tasks tasks={tasks}/>
    </div>
  );
}

export default App;
```

`Tasks.js` component

```jsx
const Tasks = ({tasks}) => {
  return (
    <>
      {tasks.map((task) => (
        <h3 key={task.id}>{task.text}</h3>
      ))}
    </>
  );
};

export default Tasks;
```

## Task Component

- create a new file `Task.js` inside `components` folder

Task.js

- represents a single task as a component

```jsx
function Task({ task }) {
    return (
        <div className='task'>
            <h3>{task.text}</h3>
            <p>{task.day}</p>
        </div>
    )
}

export default Task
```

Tasks.js

- Imports task component and displays multipe tasks

```jsx
import Task from './Task'

const Tasks = ({tasks}) => {
  return (
    <>
      {tasks.map((task) => (
        <Task key={task.id} task={task} />
      ))}
    </>
  );
};

export default Tasks;
```

## Icons with react-icons

- install `react-icons` using `npm` utility

```bash
npm i react-icons
```

- `react-icons` will now be visible as dependency inside `package.json`

- Now we can use icons as react components
- There are multiple libraries which we can use with react-icons, for eg :

```jsx
import { FaTimes } from 'react-icons/fa'
```

- Note: you will have to restart react dev server after installing `react-icons`

Example: using icons from react-icons

```jsx
import { FaTimes } from 'react-icons/fa'

function Task({ task }) {
    return (
        <div className='task'>
            <h3>
                {task.text} <FaTimes style={{ color: 'red', cursor: 'pointer' }}/>
            </h3>
            <p>{task.day}</p>
        </div>
    )
}

export default Task
```

## Delete task & prop drilling

- __Delete Task__ create a `onDelete` function in `App.js` and pass it down as prop to `Tasks.js` component and again pass it down as prop to `Task.js` component.

```jsx
  // Delete Task
  const deleteTask = (id) => {
    setTasks(tasks.filter((task) => task.id !== id))
  };
```

- `State` gets passed down, `Actions` get passed up.

Task.js component which triggers `deleteTask` and changes state additionaly changes are reflected in UI

```jsx
import { FaTimes } from "react-icons/fa";

function Task({ task, onDelete, onToggle }) {
  return (
    <div className={`task ${task.reminder ? 'reminder':''}`} onDoubleClick={() => onToggle(task.id)}>
      <h3>
        {task.text}
        <FaTimes
          style={{ color: "red", cursor: "pointer" }}
          onClick={() => onDelete(task.id)}
        />
      </h3>
      <p>{task.day}</p>
    </div>
  );
}

export default Task;
```

## Toggle reminder & conditional styling

- __Toggle Reminder__ create a `toggleReminder` function in `App.js` root component. and pass it down as prop to `Tasks.js` component and again pass it down as prop to `Task.js` component.

```jsx
  // Toggle Reminder
  const toggleReminder = (id) => {
    setTasks(
      tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      )
    );
  };
```

Task.js component which triggers `toggleReminder` and changes state additionaly changes are reflected in UI

```jsx
import { FaTimes } from "react-icons/fa";

function Task({ task, onDelete, onToggle }) {
  return (
    <div className={`task ${task.reminder ? 'reminder':''}`} onDoubleClick={() => onToggle(task.id)}>
      <h3>
        {task.text}
        <FaTimes
          style={{ color: "red", cursor: "pointer" }}
          onClick={() => onDelete(task.id)}
        />
      </h3>
      <p>{task.day}</p>
    </div>
  );
}

export default Task;
```

## Add Task Form

- Create `AddTask.js` component

```jsx
const AddTask = () => {
    return (
        <form className='add-form'>
            <div className='form-control'>
                <label>Task</label>
                <input type='text' placeholder='Add Task' />
            </div>
            <div className='form-control'>
                <label>Day & Time</label>
                <input type='text' placeholder='Add Day & Time' />
            </div>
            <div className='form-control form-control-check'>
                <label>Ser Reminder</label>
                <input type='checkbox' />
            </div>

            <input type='submit' value='Save Task' 
            className='btn btn-block'/>
        </form>
    )
}

export default AddTask
```

```jsx
import { useState } from "react";
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

function App() {
  const [tasks, setTasks] = useState([
    {
      id: 1,
      text: "Doctors Appointment",
      day: "Feb 5th at 2:30pm",
      reminder: true,
    },
    {
      id: 2,
      text: "Meeting at School",
      day: "Feb 6th at 1:30pm",
      reminder: true,
    },
    {
      id: 3,
      text: "Food Shopping",
      day: "Feb 5th at 2:30pm",
      reminder: false,
    },
  ]);

  // Delete Task
  const deleteTask = (id) => {
    setTasks(tasks.filter((task) => task.id !== id));
  };

  // Toggle Reminder
  const toggleReminder = (id) => {
    setTasks(
      tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      )
    );
  };

  return (
    <div className="contianer">
      <Header />
      <AddTask />
      {tasks.length > 0 ? (
        <Tasks tasks={tasks} onDelete={deleteTask} onToggle={toggleReminder} />
      ) : (
        "No Tasks To Show"
      )}
    </div>
  );
}

export default App;
```

## Form input state (controlled components)

- `AddTask.js` form component, Each input will have its own component level state (not app level state)

```jsx
import {useState} from 'react'

const AddTask = () => {
    const [text, setText] = useState('')
    const [day, setDay] = useState('')
    const [reminder, setReminder] = useState(false)
 
    return (
        <form className='add-form'>
            <div className='form-control'>
                <label>Task</label>
                <input type='text' placeholder='Add Task'
                value={text} 
                onChange={(e) => setText(e.target.value)}/>
            </div>
            <div className='form-control'>
                <label>Day & Time</label>
                <input type='text' placeholder='Add Day & Time'
                value={day} 
                onChange={(e) => setDay(e.target.value)} />
            </div>
            <div className='form-control form-control-check'>
                <label>Ser Reminder</label>
                <input type='checkbox' 
                value={reminder} 
                onChange={(e) => setReminder(e.currentTarget.checked)}/>
            </div>

            <input type='submit' value='Save Task' 
            className='btn btn-block'/>
        </form>
    )
}

export default AddTask
```

## Add task submit

AddTask.js

```jsx
import {useState} from 'react'

const AddTask = ({onAdd}) => {
    const [text, setText] = useState('')
    const [day, setDay] = useState('')
    const [reminder, setReminder] = useState(false)
 
    const onSubmit = (e) => {
        e.preventDefault()

        if(!text){
            alert('Please add a task')
            return
        }

        onAdd({text,day,reminder})

        setText('')
        setDay('')
        setReminder(false)
    }

    return (
        <form className='add-form' onSubmit={onSubmit}>
            <div className='form-control'>
                <label>Task</label>
                <input type='text' placeholder='Add Task'
                value={text} 
                onChange={(e) => setText(e.target.value)}/>
            </div>
            <div className='form-control'>
                <label>Day & Time</label>
                <input type='text' placeholder='Add Day & Time'
                value={day} 
                onChange={(e) => setDay(e.target.value)} />
            </div>
            <div className='form-control form-control-check'>
                <label>Ser Reminder</label>
                <input type='checkbox' 
                checked={reminder}
                value={reminder} 
                onChange={(e) => setReminder(e.currentTarget.checked)}/>
            </div>

            <input type='submit' value='Save Task' 
            className='btn btn-block'/>
        </form>
    )
}

export default AddTask
```

App.js

```jsx
import { useState } from "react";
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

function App() {
  const [tasks, setTasks] = useState([
    {
      id: 1,
      text: "Doctors Appointment",
      day: "Feb 5th at 2:30pm",
      reminder: true,
    },
    {
      id: 2,
      text: "Meeting at School",
      day: "Feb 6th at 1:30pm",
      reminder: true,
    },
    {
      id: 3,
      text: "Food Shopping",
      day: "Feb 5th at 2:30pm",
      reminder: false,
    },
  ]);

  // Add Task
  const addTask  = (task) => {
    const id = Math.floor(Math.random() * 1000) + 1
    
    const newTask = {id, ...task}
    setTasks([...tasks, newTask])
  }

  // Delete Task
  const deleteTask = (id) => {
    setTasks(tasks.filter((task) => task.id !== id));
  };

  // Toggle Reminder
  const toggleReminder = (id) => {
    setTasks(
      tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      )
    );
  };

  return (
    <div className="contianer">
      <Header />
      <AddTask onAdd={addTask} />
      {tasks.length > 0 ? (
        <Tasks tasks={tasks} onDelete={deleteTask} onToggle={toggleReminder} />
      ) : (
        "No Tasks To Show"
      )}
    </div>
  );
}

export default App;
```

## showAddTask state

- We want add button to toggle `AddTask.js` form component
- We will have another state `showAddTask` in our App component, a boolean state false by default

```jsx
const [showAddTask, setShowAddTask] = useState(false)
```

## Add Button toggle

Header.js which contains add button

```jsx
<Header onAdd={() => setShowAddTask(!showAddTask)}
      showAdd={showAddTask} />
```

Header.js

```jsx
import PropTypes from 'prop-types'
import Button from './Button'

const Header = ({ title, onAdd, showAdd }) => {
    return (
        <header className="header">
            <h1>{title}</h1>
            <Button 
                color={showAdd ? 'red' : 'green'} 
                text={showAdd ? 'Close' : 'Add'} 
            onClick={onAdd} />
        </header>
    )
}

Header.defaultProps = {
    title: 'Task Tracker',
}

Header.propTypes = {
    title: PropTypes.string.isRequired,
}

// CSS in JS
// const headingStyle = {
//     color: 'red', 
//     backgroundColor: 'black'
// }

export default Header
```

## Build for production

- Build your static assets

```bash
npm run build
```

this will create an optimized production build on `build` folder which can be deployed and it can be served via a static server:

- Install `serve` globally via `npm` utility (a basic http server)

```bash
npm i -g serve
```

- now serve your build folder on port 8000 via `serve` npm package

```bash
serve -s build -p 8000
```

## JSON Server (mock backend)

- [JSON Server](https://github.com/typicode/json-server) allows us to create mock rest api with our own data
- install `json-server` package via `npm` utility

    ```bash
    npm -i json-server
    ```

- create a script for `json-server` in package.json file

    ```json
    "scripts": {
        "start": "react-scripts start",
        "build": "react-scripts build",
        "test": "react-scripts test",
        "eject": "react-scripts eject",
        "server": "json-server --watch db.json --port 5000"
    },
    ```

- now run server script using `npm`

    ```bash
    npm run server
    ```

- this will create `db.json` on your repo

- start react dev server on a new terminal window

    ```bash
    npm start 
    ```

- move your `tasks` objects from `App.js` to `db.json`

    ```jsx
    const [tasks, setTasks] = useState([]);
    ```

    ```db.json
    {
    "tasks": [
        {
        "id": 1,
        "text": "Doctors Appointment",
        "day": "Feb 5th at 2:30pm",
        "reminder": true
        },
        {
        "id": 2,
        "text": "Meeting at School",
        "day": "Feb 6th at 1:30pm",
        "reminder": true
        },
        {
        "id": 3,
        "text": "Food Shopping",
        "day": "Feb 5th at 2:30pm",
        "reminder": false
        }
    ]
    }

    ```

## useEffect Hook & Fetch tasks from server

- `useEffect` hook can be used to load data on page load.
- `useEffect` is used to create side effects or deal with side effects and is often used to do stuff when page loads
- `useEffect` takes in an arrow function, we will use fetch api with async await

```jsx
import { useState, useEffect } from "react";
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

function App() {

  const [showAddTask, setShowAddTask] = useState(false)
  const [tasks, setTasks] = useState([]);

  useEffect(() => {
    const getTasks = async() => {
      const tasksFromServer = await fetchTasks()
      setTasks(tasksFromServer)
    }
    getTasks()
  }, [])

  // Fetch Tasks 

  const fetchTasks = async () => {
    const res = await fetch('http://localhost:5000/tasks')
    const data = await res.json()

    return data
  }


  // Add Task
  const addTask  = (task) => {
    const id = Math.floor(Math.random() * 1000) + 1
    
    const newTask = {id, ...task}
    setTasks([...tasks, newTask])
  }

  // Delete Task
  const deleteTask = async (id) => {
    await fetch(`http://localhost:5000/tasks/${id}`, {
        method: 'DELETE',
    })

    setTasks(tasks.filter((task) => task.id !== id));
  };

  // Toggle Reminder
  const toggleReminder = (id) => {
    setTasks(
      tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      )
    );
  };

  return (
    <div className="contianer">
      <Header onAdd={() => setShowAddTask(!showAddTask)}
      showAdd={showAddTask} />
      {showAddTask && <AddTask onAdd={addTask} />}
      {tasks.length > 0 ? (
        <Tasks tasks={tasks} onDelete={deleteTask} onToggle={toggleReminder} />
      ) : (
        "No Tasks To Show"
      )}
    </div>
  );
}

export default App;
```

## Delete task from server

```jsx
  // Delete Task
  const deleteTask = async (id) => {
    await fetch(`http://localhost:5000/tasks/${id}`, {
      method: 'DELETE'
    })
    
    setTasks(tasks.filter((task) => task.id !== id));
  };
```

## Add task to server

```jsx
  // Add Task
  const addTask  = async (task) => {
    const res = await fetch('http://localhost:5000/tasks', {
      method: 'POST',
      headers: {
        'Content-type': 'application/json'
      },
      body: JSON.stringify(task)
    })

    const data = await res.json()

    setTasks([...tasks, data])

    // const id = Math.floor(Math.random() * 1000) + 1
    
    // const newTask = {id, ...task}
    // setTasks([...tasks, newTask])

  }
```

## Toggle reminder on server

```jsx
  // Fetch Task
  const fetchTask = async (id) => {
    const res = await fetch(`http://localhost:5000/tasks/${id}`)
    const data = await res.json()

    return data
  }

    // Toggle Reminder
    const toggleReminder = async (id) => {
        const taskToToggle = await fetchTask(id)
        const updTask = {...taskToToggle, reminder: !taskToToggle.reminder}

        const res = await fetch(`http://localhost:5000/tasks/${id}`, {
            method: 'PUT',
            headers: {
            'Content-Type': 'application/json',
            },
            body: JSON.stringify(updTask),
        })

        const data = await res.json()

        setTasks(
            tasks.map((task) =>
            task.id === id ? { ...task, reminder: data.reminder } : task
          )
        );
    };

```

## Routing, footer & about

- There is no routing in root react library
- we can add a package `react-router-dom`

    ```bash
    npm i react-router-dom
    ```

- use `BrowserRouter as Router` and `Route` from `react-router-dom`

- wrap return around `<Router></Rotuer>` tag
- use `Link` from `react-router-dom` instaed of anchor tags to prevent reloading of browser

App.js

```jsx
import { useState, useEffect } from "react";
import {BrowserRouter as Router, Route} from 'react-router-dom'
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";
import Footer from "./components/Footer";
import About from "./components/About";

function App() {

  const [showAddTask, setShowAddTask] = useState(false)
  const [tasks, setTasks] = useState([]);

  useEffect(() => {
    const getTasks = async() => {
      const tasksFromServer = await fetchTasks()
      setTasks(tasksFromServer)
    }
    getTasks()
  }, [])

  // Fetch Tasks 
  const fetchTasks = async () => {
    const res = await fetch('http://localhost:5000/tasks')
    const data = await res.json()

    return data
  }

  // Fetch Task
  const fetchTask = async (id) => {
    const res = await fetch(`http://localhost:5000/tasks/${id}`)
    const data = await res.json()

    return data
  }

  // Add Task
  const addTask  = async (task) => {
    const res = await fetch('http://localhost:5000/tasks', {
      method: 'POST',
      headers: {
        'Content-type': 'application/json'
      },
      body: JSON.stringify(task)
    })

    const data = await res.json()

    setTasks([...tasks, data])

    // const id = Math.floor(Math.random() * 1000) + 1
    
    // const newTask = {id, ...task}
    // setTasks([...tasks, newTask])

  }

  // Delete Task
  const deleteTask = async (id) => {
    await fetch(`http://localhost:5000/tasks/${id}`, {
      method: 'DELETE'
    })

    setTasks(tasks.filter((task) => task.id !== id));
  };

  // Toggle Reminder
  const toggleReminder = async (id) => {
    const taskToToggle = await fetchTask(id)
    const updTask = {...taskToToggle, reminder: !taskToToggle.reminder}

    const res = await fetch(`http://localhost:5000/tasks/${id}`, {
      method: 'PUT',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(updTask),
    })

    const data = await res.json()

    setTasks(
      tasks.map((task) =>
        task.id === id ? { ...task, reminder: data.reminder } : task
      )
    );
  };

  return (
    <Router>
      <div className="contianer">
        <Header onAdd={() => setShowAddTask(!showAddTask)}
        showAdd={showAddTask} />

        <Route path='/' exact render={(props) => (
          <>
            {showAddTask && <AddTask onAdd={addTask} />}
            {tasks.length > 0 ? (
              <Tasks tasks={tasks} 
                onDelete={deleteTask} 
                onToggle={toggleReminder} />
            ) : (
              "No Tasks To Show"
            )}
          </>
        )} />
        <Route path='/about' component={About}/>
        <Footer />
      </div>
    </Router>
  );
}

export default App;
```

About.js

```jsx
import {Link} from 'react-router-dom'

const About = () => {
    return (
        <div>
            <h4>Version 1.0.0</h4>
            <Link to="/">Go Back</Link>
        </div>
    )
}

export default About
```

Header.js

```jsx
import PropTypes from 'prop-types'
import {useLocation} from 'react-router-dom'
import Button from './Button'

const Header = ({ title, onAdd, showAdd }) => {
    const location = useLocation()
    return (
        <header className="header">
            <h1>{title}</h1>
            {location.pathname === '/' && <Button 
                color={showAdd ? 'red' : 'green'} 
                text={showAdd ? 'Close' : 'Add'} 
            onClick={onAdd} />}
        </header>
    )
}

Header.defaultProps = {
    title: 'Task Tracker',
}

Header.propTypes = {
    title: PropTypes.string.isRequired,
}

export default Header
```
