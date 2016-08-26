## How to setup ReactJS environment

### Prerequisites
1. Install Xcode
2. Install hombrew
	
		> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
		
3. Install Node

		> brew install node

### ReactJS

1. Install global packages. We will need some of the babel plugins so let's first install babel by running the following code in command prompt window.

		> npm install -g babel
		> npm install -g babel-cli
		
2. Create root folder

		> mkdir reactApp
		> cd reactApp
		> npm init
		
3. Add dependencies and plugins

	a) We will use webpack bundler in these tutorials so let's install webpack and webpack-dev-server:
	
		> npm install webpack --save
		> npm install webpack-dev-server --save
		
	b) Since we want to use React, we need to install it first. The --save command will add these packages to package.json file.	
	
		> npm install react --save
		> npm install react-dom --save
		
	c) We already mentioned that we will need some babel plugins so let's install it too.
	
		> npm install babel-core
		> npm install babel-loader
		> npm install babel-preset-react
		> npm install babel-preset-es2015
		
4. Let's create several files that we need. You can add it manually or you can use command prompt.

		> touch index.html
		> touch App.jsx
		> touch main.js
		> touch webpack.config.js

5. Set Compiler, Server and Loaders

	a) Update webpack.config.js
	
		var config = {
		   entry: './main.js',
			
		   output: {
		      path:'./',
		      filename: 'index.js',
		   },
			
		   devServer: {
		      inline: true,
		      port: 8080
		   },
			
		   module: {
		      loaders: [
		         {
		            test: /\.jsx?$/,
		            exclude: /node_modules/,
		            loader: 'babel',
						
		            query: {
		               presets: ['es2015', 'react']
		            }
		         }
		      ]
		   }
		}
		
		module.exports = config;
		
	b) Update package.json
		
	Replace the following line:
	
		"test": "echo \"Error: no test specified\" && exit 1"
		
	With the following line:
		
		"start": "webpack-dev-server --hot"

	Note: We are deleting this line since we will not do any testing in this tutorials.
	
6. Create index.html

		<!DOCTYPE html>
		<html lang = "en">
		
		   <head>
		      <meta charset = "UTF-8">
		      <title>React App</title>
		   </head>
		
		   <body>
		      <div id = "app"></div>
		      <script src = "index.js"></script>
		   </body>
		
		</html>
		
7. App.jsx and main.js

	This is the first react component. We will explain React components in depth in one of our later tutorials. This component will render Hello World!!!.
	
	App.jsx
	
		import React from 'react';

		class App extends React.Component {
		   render() {
		      return (
		         <div>
		            Hello World!!!
		         </div>
		      );
		   }
		}
		
		export default App;
		
	main.js
	
		import React from 'react';
		import ReactDOM from 'react-dom';
		import App from './App.jsx';
		
		ReactDOM.render(<App />, document.getElementById('app'));
		
	NOTE: Whenever you want to use something, you need to import it first. If you want to make component usable in other parts of the app, you need to export it after creation and import it in the file where you want to use it.
	
8. Running the server
	
	The setup is finished and we can start the server by running:
	
		> npm start
		
	You can now see the result by accessing:
	
		> http://localhost:8080
	
	Note: The port number is based on the what you specified in the webpack.config.js.