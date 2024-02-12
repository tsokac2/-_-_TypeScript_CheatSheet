<h1 align="center">Webpack with TypeScript</h1>

### Overview of the Section
* **[What is Webpack & Why do we need it?](#webpack)**
* **[Installing Webpack & Important Dependencies](#install)**
* **[Adding a Production Workflow](#production)**

https://webpack.js.org/

#
### <a name="webpack">What is Webpack & Why do we need it?</a>

Webpack helps you build cleaner, more efficient, and maintainable JavaScript applications by organizing your code, optimizing bundled files, and supporting modern development practices.

**Here's why Webpack is valuable**:

- **Organization**: It keeps your codebase organized and manageable, making it easier to collaborate and maintain.
- **Efficiency**: Webpack optimizes the bundled files, reducing their size and improving loading times for your website.
- **Modularization**: It promotes code reusability by allowing you to share modules across different parts of your application.
- **Flexibility**: Webpack supports various loaders and plugins, allowing you to transform different types of assets (CSS, images, etc.) and integrate them into your bundles.
- **Modern features**: Webpack can handle modern JavaScript features like ES6 modules and transpile them into formats compatible with older browsers.
#

![webpack](https://github.com/tsokac2/-_-_TypeScript_CheatSheet/blob/main/src/04.JPG)

**[Back To The Top](#Overview-of-the-Section)**

### <a name="install">Installing Webpack & Important Dependencies</a>

- **Webpack**: This is the core tool that allows you to bundle and transform your code. It's crucial for optimizing your project's workflow.

- **Webpack CLI**: This is the command-line interface for running Webpack commands in your project. It's essential for executing various Webpack functionalities.

- **Webpack Dev Server**: This package provides a built-in development server. It watches your files for changes, triggers Webpack to recompile when necessary, and auto-serves your page. It's a handy tool for a smooth development experience.

- **TypeScript**: TypeScript is a superset of JavaScript that adds static typing to your code. It helps catch errors during development and enhances code maintainability.

- **ts-loader**: This package works in conjunction with Webpack. It instructs Webpack on how to convert TypeScript code to JavaScript, enabling Webpack to compile and bundle your code effectively.

```
npm install --save-dev webpack webpack-cli webpack-dev-server typescript ts-loader
```
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="install">Installing Webpack & Important Dependencies</a>

1. **tsconfig.json Configuration**:
- It's good that you are configuring the ``tsconfig.json`` file. Setting the target to either ``es5`` or ``es6`` depends on your target browser compatibility. It's a crucial decision, especially if you have specific browser requirements.
- The module set to ``es2015`` or ``es6`` is a standard configuration.
- Verifying the outDir is also important, and your decision to keep it as dist aligns with common practices.

2. **webpack.config.js Configuration**:
- Creating a ``webpack.config.js`` file is a necessary step to instruct webpack on how to handle your project.
- Defining the entry point using app.ts makes sense, as it's typically the starting point for your application.
- Naming the output file as bundle.js is a standard convention. The dynamic options like content hash for caching are optional but useful, as you rightly pointed out.
- Specifying the absolute path for the output folder is crucial. Using path.resolve with __dirname ensures a robust and accurate path.

3. **Importing Modules and Handling Extensions**:
- Removing ``.js`` extensions in imports is a key insight. With webpack, it handles the resolution automatically, simplifying your import statements.

4. **Compiling TypeScript with webpack**:
- Your mention of the need to teach webpack how to handle TypeScript files is spot on. It's essential to introduce the TypeScript loader to webpack, ensuring it understands how to transpile TypeScript into JavaScript.

#### webpack.config.js
```
const path = require('path');
 
module.exports = {
  mode: 'development',
  entry: './src/app.ts',
  devServer: {
    static: [
      {
        directory: path.join(__dirname),
      },
    ],
  },
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
    publicPath: '/dist/',
  },
  module: {
    rules: [
      {
        test: /\.tsx?$/,
        use: 'ts-loader',
        exclude: /node_modules/,
      },
    ],
  },
  resolve: {
    extensions: ['.ts', '.js'],
  },
};
```
#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="production">Adding a Production Workflow</a>

####
```
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "webpack-dev-server",
    "build": "webpack --config webpack.config.prod.js"
  },
```

#### webpack.config.prod.js
```
const path = require('path');
const CleanPlugin = require('clean-webpack-plugin');
 
module.exports = {
  mode: 'production',
  entry: './src/app.ts',
  devServer: {
    static: [
      {
        directory: path.join(__dirname),
      },
    ],
  },
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist')
  },
  devtool: 'cheap-module-source-map',
  module: {
    rules: [
      {
        test: /\.tsx?$/,
        use: 'ts-loader',
        exclude: /node_modules/,
      },
    ],
  },
  resolve: {
    extensions: ['.ts', '.js'],
  },

  plugins: [
    new CleanPlugin.CleanWebpackPlugin()
  ]
};
```
#
**[Back To The Top](#Overview-of-the-Section)**