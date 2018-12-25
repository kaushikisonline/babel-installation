# babel-installation
This file includes all commands for installation of babel and the relevant files - .babelrc, webpack.config.js, package.json.
Install babel files using the following commands:

npm install @babel/core --save-dev
npm install --save-dev @babel/preset-env
npm install babel-loader --save-dev
npm install @babel/polyfill --save



Your webpack.config.js file should look like this:
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
    entry: ['@babel/polyfill', './src/js/index.js'],
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'js/bundle.js'
    },
    devServer: {
        contentBase: './dist',
        host: '127.0.0.1',
        port: 8080,
        https: false,
        disableHostCheck: true
    },
    plugins: [
        new HtmlWebpackPlugin ({
            filename: 'index.html',
            template: './src/index.html'
        })
    ],
    module: {
        rules: [
            {
                test: /\.js$/,
                exclude: /node_modules/,
                use: {
                    loader: 'babel-loader'
                }
            }
        ]
    }
};




Your .babelrc file should look like this:
{
    "presets": [
        ["@babel/env", {
            "targets": {
                "browsers": [
                    "last 5 versions",
                    "ie >= 8"
                ]
            }
        }]
    ]
} 




Your package.json file should look like this:
{
  "name": "forkify",
  "version": "1.0.0",
  "description": "forkify project",
  "main": "index.js",
  "scripts": {
    "dev": "webpack --mode development",
    "build": "webpack --mode production",
    "start": "webpack-dev-server --mode development --open"
  },
  "author": "Kaushik",
  "license": "ISC",
  "devDependencies": {
    "@babel/core": "^7.2.2",
    "@babel/preset-env": "^7.2.3",
    "babel-loader": "^8.0.4",
    "html-webpack-plugin": "^3.2.0",
    "webpack": "^4.28.2",
    "webpack-cli": "^3.1.2",
    "webpack-dev-server": "^3.1.14"
  },
  "dependencies": {
    "@babel/polyfill": "^7.2.5"
  }
}

