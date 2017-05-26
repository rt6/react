# App with React FrontEnd and Express backend

```sh
# create back-end
$ npm install -g express-generator
$ express react-backend
$ cd react-backend && npm i

# create front-end
$ npm install -g create-react-app
$ create-react-app client

```

Add proxy in React in `client/package.json`:

```js
"scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject"
  },
  "proxy": "http://localhost:3001"
```


If you are not developing on local machine but using EC2 and Nginx, then create `client/.env`:
```js
PORT=0
```

nginx configs
```
location / {
  proxy_pass http://127.0.0.1:3000/;
  proxy_set_header X-Real-IP $remote_addr;
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  proxy_set_header X-NginX-Proxy true;
  roxy_redirect off;
}
```

React can fetch data from Express REST API:
```js
import React, { Component } from 'react';
import './App.css';

class App extends Component {
  state = {friends: []}

  componentDidMount() {
    fetch('/friends')
      .then(res => res.json())
      .then(friends => this.setState({ friends }));
  }

  render() {
    return (
      <div className="App">
        <h1>Friends</h1>
        {this.state.friends.map(user =>
          <div key={friend.id}>{friend.username}</div>
        )}
      </div>
    );
  }
}

export default App;
```


Start Express and React Dev Server:
```sh
# you can also use concurrently from NPM
$ cd react-backend && PORT=3001 node bin/www
$ cd client && npm start
```
