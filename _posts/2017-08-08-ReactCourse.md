---
layout: post #post
title: React Course and Build a Book Store #post title
categories: React  #post category, seperated by space
tags: React Front-end Coursera JavaScript #post tag, seperated by space
---


*Udemy course*


### 1. why redux

1. Application state, store all components' state, children components get these states by this.props. children components can also have its state 

2. State container, store application states.

3. Setup:

4. Workflow: 

   store(create and maintain states)-->
   
   provider(passing down store as props)-->
   
   actions(fire actions to update states)-->
   
   middleware(optional, useful when create a kind of chain of action when the action reaches the user which evaluates what to do with the action)-->
   
   reducers(update the data in the store which then updates the app)-->
   
   store(so on in a cycle)
   
5. Middleware: hook function
 
### 2. setup 
 
1. Install express, webpack, babel

    ```
    npm init
    npm i --save express
    npm i --save webpack
    npm i --save babel-core babel-loader babel-preset-es2015 babel-preset-stage-1 babel-preset-react
    npm i --save redux
    ```
  
2. Design file tree:

    ```
    -- AppFile
        - node_modulus(folder)
        - public(folder)
        - index.html
        - src(folder)
        - app.js
        - package.json
        - server.js
        - webpack.config.js   
    ```
 
3. Write server.js

    - require() function 

        - loads a module and assigns it to a variable for your application to use

        - to access functionality located in other files in your project.

        - In Node module system each of your javascript file is a module and can expose functionality to be required by other files.
    
    - Express: 

        - Express in nodejs is a framework which provides features like: Middlewares to respond to your request, Routing, Render html web pages. 
        
        - Routing: handle multiple url context in a website, or how they respond to client requests.
        
        - Route paths can be strings, string patterns, or regular expressions.
        
        - Middleware functions are functions that have access to the request / response objects, and the next middleware function in the application’s request-response cycle. 
        
        - Serving Static Files: Express provides a built-in middleware express.static to serve static files, such as images, CSS, JavaScript etc

    -  Using "use strict" directive to make sure you receive an error, writing js need to specify "use strict", writing jsx, use strict is default

    - So the server.js is like:

        ```
        "use strict"
        var express = require('express');
        var app = express();
        var path = require('path');

        //middleware to define folder for strict files or images
        app.use(express.static('public'));

        //catch the main route, send back response as index.html
        app.get('/', function(req,res){
            res.sendFile(path.resolve(__dirname,'public','index.html'))
        });

        app.listen(3000,function(){
            console.log('listening 3000');
        });
        ```

4. Config webpack, webpack.config.js

    - We make our module available using module.exports

    - Watch: true. So that every time we save our changes in one of the files are linked with the app.js, webpack will recompile the bundle file automatically

    ```
    var path = require('path');
    const webpack = require('webpack');

    module.exports = {
        //path of our js file; 
        entry: './src/app.js',
        output: {
            filename: 'bundle.js',
            path: path.resolve(__dirname,'public')
        },
        watch: true,
        module:{
            loaders:[
                {
                    //scan all js files, to prevent long compile time, we exclude the old js files inside
                    test: /\.js$/,
                    exclude: /node_modules/,
                    loader: 'babel-loader',
                    query: {
                        presets: ['react','es2015','stage-1']
                    }
                }
            ]
        }
    }
    ```

5. Start. Start node and webpack, go to localhost:3000

    ```
    node server.js
    webpack
    ```

### 3. Create app

1. Import createStore module from redux

2. Create store using reducer

    - Pass the reducers as argument to create store

    - See what the store's current state, using subscript method

    - Lock the result using store.getState()

3. Create and dispatch actions

    - An action is made by an object that has two properties: type and payload
    
    - Type is a keyword in redux, but payload you can call it as you wish

    - Create a counter : `store.dispatch({type:"INCREMENT", payload:1})`


4. Define reducers

    - Create reducer by passing two arguments, state and action

    - reducer is used to evaluate what to du when they receive an action

