# How to make a Hello World JS/React website :

* Install NPM and Node (Node comes with NPM? You might only need to install NPM)
* Install React.js : npm install --save-dev react react-dom
* You also need to : npm install --save-dev react react-dom
** JS is insane - don't use -g to install globally because it can't find it; dev-dependencies are a separate set to runtime dependencies (not a superset) so those need to be installed with the correct flag. NPM packages are not like Ruby gems! 
* In the base folder for your website : npm init --yes

* npm install --save-dev @babel/core @babel/preset-env
* npm install --save-dev babel-loader@7
* npm install --seve-dev babel-preset-es2015 babel-preset-react

* npm install -g webpack
* npm install -g webpack-cli
* npm link webpack
* Create a file called .babelrc with contents :
```
{                                    
  "presets" : ["es2015", "react"]    
}   
```

* Create a file called webpack.config.js with contents : 
```
const path = require('path');
 
module.exports = {
  entry: './app/index.js',
  output: {
    path: path.resolve('dist'),
    filename: 'index_bundle.js'
  },
  module: {
    rules: [
      { test: /\.js$/, loader: 'babel-loader', exclude: /node_modules/ }
    ]
  }
}
```

* Create a subfolder for your application (e.g. 'app')
* In the subfolder, create a file called index.js with contents : 
```
import React from 'react';
import ReactDOM from 'react-dom';
 
class HelloWorld extends React.Component {
    render() {
          return (
                  <div>
                    Hello World
                  </div>
                )
        }
};
 
ReactDOM.render(<HelloWorld />, document.getElementById('root'));
```

* In the base folder, create index.html with contents : 
```
<html>
  <div id="root"></div>
  <script src="./dist/index_bundle.js"></script>
</html>
```

In the base folder, run : webpack
