# REACT


### Bootstrap
1. create `/index.html`
2. create `/package.json`
3. create `/webpack.config.js`
3. run `npm i`
4. start coding app in `/source/app.js`


# index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>First React Component</title>
</head>
<body>
    <div id="root"></div>
    <script type="text/javascript" src="bundle.js"></script>
</body>
</html>
```

# package.json
```js
{
  "name": "your-app-name",
  "version": "1.0.0",
  "description": "your-app-description",
  "main": "index.js",
  "scripts": {
    "start": "node_modules/.bin/webpack-dev-server --progress"
  },
  "author": "you",
  "dependencies": {
    "react": "^15.5.4"
  },
  "devDependencies": {
    "babel-core": "^6.24.1",
    "babel-loader": "^7.0.0",
    "webpack": "^2.5.1",
    "webpack-dev-server": "^2.4.5"
  }
}
```

# webpack.config.js
```js
module.exports = {
    entry: [
        './source/App.js'
    ],
    output: {
        path: __dirname,
        filename: "bundle.js"
    },
    module: {
        loaders: [{
            test: /\.jsx?$/,
            loader: 'babel'
        }]
    }
};
```
