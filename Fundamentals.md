# React and Javascript Classes

```
class Developer {
    constructor(firstname, lastname) {
        this.firstname = firstname;
        this.lastname = lastname;
    }

    getName() {
        return this.firstname + ' ' + this.lastname;
    }
}

var me = new Developer('Avicenna', 'Mojo');
console.log(me.getName())
```
The above is basically python. Inheritance:
```
class ReactDeveloper extends Developer {
    getJob() {
        return 'React Developer';
    }
}

var me = new ReactDeveloper('Mojo', 'Avicenna');
console.log(me.getJob())
```
Now compare the above with react components:
```
import React, { Component } from 'react';

class App extends Component {
    render() {
        return (
            <div>
            <h1>Welcome to React</h1>
            </div>
        );
    }
}

export default App;
```
So basically, react components are javascript classes that inherit from the react package. You can even customize with your own special methods as such:
```
import React, { Component } from 'react';

class App extends Component {
    getGreeting() {
        return 'Welcome to React';
    }
    render() {
        return (
            <div>
            <h1<{this.getGreeting()}</h1>
            </div>
        );
    }
}

export default App;
```
React uses javascript classes for defining React class components. However, react components can be defined in a different way without using a javascript class and this is a better method because react favors composition over inheritance. The only class you should extend from your react components should be the official react component.

# Arrow functions in React

```
const getGreeting = () => {
    return 'Welcome to JS';
}
//Alternatively
const getGreeting = () => 'Welcome to Javascript';
```

# Funtions as components in React
```
// Generally
function (props) {
  return view;
}

// JavaScript ES5 function
function Greeting(props) {
  return <h1>{props.greeting}</h1>;
}

// JavaScript ES6 arrow function
const Greeting = (props) => {
  return <h1>{props.greeting}</h1>;
}

// JavaScript ES6 arrow function
// without body and implicit return
const Greeting = (props) =>
  <h1>{props.greeting}</h1>;
```
# React Class Component Syntax

There exists many syntax for React class components
```
class Counter extends Component {
  constructor(props) {
    super(props);

    this.state = {
      counter: 0,
    };

    this.onIncrement = this.onIncrement.bind(this);
    this.onDecrement = this.onDecrement.bind(this);
  }

  onIncrement() {
    this.setState(state => ({ counter: state.counter + 1 }));
  }

  onDecrement() {
    this.setState(state => ({ counter: state.counter - 1 }));
  }

  render() {
    return (
      <div>
        <p>{this.state.counter}</p>

        <button
          onClick={this.onIncrement}
          type="button"
        >
          Increment
        </button>
        <button
          onClick={this.onDecrement}
          type="button"
        >
          Decrement
        </button>
      </div>
    );
  }
}
```

A simpler version of the above:
```
class Counter extends Component {
  state = {
    counter: 0,
  };

  onIncrement = () => {
    this.setState(state => ({ counter: state.counter + 1 }));
  }

  onDecrement = () => {
    this.setState(state => ({ counter: state.counter - 1 }));
  }

  render() {
    return (
      <div>
        <p>{this.state.counter}</p>

        <button
          onClick={this.onIncrement}
          type="button"
        >
          Increment
        </button>
        <button
          onClick={this.onDecrement}
          type="button"
        >
          Decrement
        </button>
      </div>
    );
  }
}
```
By using JavaScript arrow functions, you can auto-bind class methods without having to bind them in the constructor.

# Template literals in React

Basically f-strings in python
```
function getGreeting(what) {
  return `Welcome to ${what}`;
}
```

# Map, Reduce and Filter in React
```
import React from 'react';

const App = () => {
  var user = { name: 'Robin' };
  return (
    <div>
      <h1>{user.name}</h1>
    </div>
  );
}

export default App;
```
To render a list of items use vanilla Js
```
import React from 'react';

const App = () => {
  var users = [
    { name: 'Avicenna' },
    { name: 'Mojo' },
  ];

  return (
    <ul>
      {users.map(function (user) {
        return <li>{user.name}</li>;
      })}
    </ul>
  );
};

export default App;
```
Even easier:
```
import React from 'react';

const App = () => {
  var users = [
    { name: 'Avicenna' },
    { name: 'Mojo' },
  ];

  return (
    <ul>
      {users.map(user => <li>{user.name}</li>)}
    </ul>
  );
};

export default App;
```
You can filter() in the same way:
```
import React from 'react';

const App = () => {
  var users = [
    { name: 'Avicenna', isDeveloper: true },
    { name: 'Mojo', isDeveloper: false },
  ];

  return (
    <ul>
      {users
      .filter(user => user.isDeveloper)
      .map(user => <li>{user.name}</li>)}
    </ul>
  );
};

export default App;
```
# Var, Let and Const in React

Rules of thumb when to use which variable declaration:

    (1) don't use var anymore, because let and const are more specific
    (2) default to const, because it cannot be re-assigned or re-declared
    (3) use let when re-assigning the variable

While let is usually used in a for loop for incrementing the iterator, const is normally used for keeping JavaScript variables unchanged. Even though it is possible to change the inner properties of objects and arrays when using const, the variable declaration shows the intent of keeping the variable unchanged though.

# Ternary operators
```
import React from 'react';

const App = () => {
  const users = [
    { name: 'Avi' },
    { name: 'Mojo' },
  ];

  const showUsers = false;

  return (
    <div>
      {showUsers ? ( // if true return users
        <ul>
          {users.map(user => (
            <li>{user.name}</li>
          ))}
        </ul>
      ) : null} // return null if false
    </div>
  );
};

export default App;
```

# Import and Export Statements

```
const firstname = 'Robin';
const lastname = 'Wieruch';

export { firstname, lastname };
```
Then you can import them in another file with a relative path to the first file:
```
import { firstname, lastname } from './file1.js';

console.log(firstname);
// output: Robin
```
Alternatively:
```
import * as person from './file1.js';

console.log(person.firstname);
// output: Robin
```
Imports can also have aliases like python:
```
import { firstname as username } from './file1.js';

console.log(username);
// output: Robin
```
All the previous cases are named imports and exports. But there exists the default statement too. It can be used for a few use cases:

    - to export and import a single functionality
    - to highlight the main functionality of the exported API of a module
    - to have a fallback import functionality
```
const robin = {
  firstname: 'Robin',
  lastname: 'Wieruch',
};

export default robin;
```
Leave out the curly braces for the import to import the default export:
```
import developer from './file1.js';

console.log(developer);
// output: { firstname: 'Robin', lastname: 'Wieruch' }
```
And so on and so forth

# Libraries
To extend functionality:
```
import React, { Component } from 'react';
import axios from 'axios';

class App extends Component {
  state = {
    data: null,
  };

  componentDidMount() {
    axios.get('https://api.mydomain.com')
      .then(response => this.setState({ data: response.data }));
  }

  render() {
    ...
  }
}

export default App;
```

# Async and Await

```
import React from 'react';
import axios from 'axios';

const App = () => {
  const [data, setData] = React.useState(null);

  React.useEffect(() => {
    const fetchData = async () => {
      const response = await axios.get('https://api.mydomain.com');

      setData(response.data);
    };

    fetchData();
  }, []);

  return (
    ...
  );
};

export default App;
```
They say promises in javascript lol

# Higher order functions in React

```
import React from 'react';

const App = () => {
  const users = [{ name: 'Robin' }, { name: 'Markus' }];
  const [query, setQuery] = React.useState('');

  const handleChange = event => {
    setQuery(event.target.value);
  };

  return (
    <div>
      <ul>
        {users
          .filter(user => user.name.includes(query))
          .map(user => (
            <li>{user.name}</li>
          ))}
      </ul>

      <input type="text" onChange={handleChange} />
    </div>
  );
};

export default App;
```
Will learn more about these when I need them
