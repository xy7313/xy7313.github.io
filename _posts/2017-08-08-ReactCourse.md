---
layout: post #post
title: React Course and Build a Book Store #post title
categories: React  #post category, seperated by space
tags: React Front-end Coursera JavaScript #post tag, seperated by space
---


*Udemy course*


## 1. why redux

1. Application state, store all components' state, children components get these states by this.props. 

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
            - index.html//include bundle.js in script tags
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

        //catch the main route, send back response in index.html
        app.get('/', function(req,res){
            res.sendFile(path.resolve(__dirname,'public','index.html'))
        });

        app.listen(3000,function(){
            console.log('listening 3000');
        });
        ```

4. Config webpack, webpack.config.js

    - We make our module available outside using module.exports

    - Watch: true. So that every time we save our changes in one of the files are linked with the app.js, webpack will recompile the bundle file automatically

    - scan all js files, to prevent long compile time, we exclude the old js files inside node_modules

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

5. Try the subscribe method, our listener in app.js

    ```
    "use strict";
    import { createStore } from "redux";

    //step 3 define reducers in order to create the store
    //create reducer by passing two arguments, set the initial value for the state
    //set initial value to state in function()
    //the use of reducers are evaluate what to do using switch
    const reducer = function(state = 0, action) {
    console.log("reducer...state: ", state, "action: ", action);
    switch (action.type) {
        case "INCREMENT":
        return state + action.payload;
        break;
        case "decrement":
        return state - action.payload;
        break;
    }
    return state;
    };

    //step 1 create the store, pass reducers as parameter
    //see the current of store, use the subscript method, add listener,
    const store = createStore(reducer);
    console.log("store: ", store);
    store.subscribe(function() {
    console.log("current state: " + store.getState());
    });

    //step 2 create and dispatch actions
    //an action is made by an object that has two properties, type and payload
    //type, key words in redux, payload, call it as you wish
    store.dispatch({ type: "INCREMENT", payload: 1 });

    store.dispatch({ type: "INCREMENT", payload: 1 });

    store.dispatch({ type: "decrement", payload: 1 });
    ```

6. When we have complex payload with actions:

    ```
    "use strict";
    import { createStore } from "redux";

    //reducer
    //when payload is an array, state = [], when payload only have one obj, state = {}
    const reducer = function(state = [], action) {
    switch (action.type) {
        case "post_book":
        return state = action.payload;
        break;
    }
    return state;
    };

    //store,state
    const store = createStore(reducer);
    store.subscribe(function() {
    // console.log("current state: " , store.getState().price);
    //when the payload is an array:
    console.log("current state: " , store.getState()[1].price);

    });

    //action
    store.dispatch({
    type:"post_book",
    payload:[
        {
        id:1,
        title:'book title',
        description:'im a book',
        price:10000
        },
        {
        id:2,
        title:'book title2',
        description:'im another book',
        price:10002
        }
    ]
    });
    ```

7. CRUD operations, (create, read, update, delete)
    ```
    const reducer = function(state = {books:[]}, action) {
        switch (action.type) {
            case "post_book":
            //we want add third book in, with out this concat, third book overwrite previous payload,
            //never use push to concatenate array in redux, use concat method, 
            //because, push is a mutable, in redux, should never mutate the state
            // let books = state.books.concat(action.payload);
            // return {books};
            return {books:[...state.books,...action.payload]}
            break;
        }
        return state;
    };
    ```
destruct??

8. Pure function, give the same input, always output the same output. Reducer should be pure function.

9. Three principles of redux

    1. Single source of truth: the state of whole app is stored in an object tree within a single store(under one object - state)

    2. States are read-only: The only way to change the state is to emit an action

    3. Changes are made with pure functions: reducers hae to be pure functions

10. prevent mute state mutation. 

    1. Operate arrays: concat(), slice() or ...spread operator, ~~push(),splice()~~

    2. Operate objects: Object.Assign() or ...spread operator

11. Delete

    ```
    //when all in one file
    //action, we can write a sequence dispatches of actions
    store.dispatch({
        type:"post_book",
        payload:[
            {
            id:1,
            title:'book title',
            description:'im a book',
            price:10000
            },
            {
            id:2,
            title:'book title2',
            description:'im another book',
            price:10002
            }
        ]
    });

    //we using logger,so we can remove subscribe method
    const store = createStore(reducers, middleware);
    store.subscribe(function() {
        console.log("current state: " , store.getState());
        // console.log("current state: " , store.getState().price);
        // when the payload is an array:
        // console.log("current state: " , store.getState()[1].price);

        });

    store.dispatch({
        type:"post_book",
        payload:[
            {
            id:3,
            title:'book title3',
            description:'im a 3rd book',
            price:10003
            },
        ]
    });
    store.dispatch({
        type:"delete_book",
        payload:{id:1}, 
        });

        store.dispatch({
        type:"update_book",
        payload:
            {
            id:2,
            title:'book title updated'
            }
    });

    store.dispatch({
        type:"add_to_cart",
        payload:[{id:1}]
        });


    //reducer
    //when payload is an array, state = [], when payload only have one obj, state = {}
    const reducer = function(state = {books:[]}, action) {
        switch (action.type) {
            case "post_book":
            //we want add third book in, with out this concat, third book overwrite previous payload,
            //never use push to concatenate array in redux, use concat method, 
            //because, push is a mutable, in redux, should never mutate the state
            // let books = state.books.concat(action.payload);
            // return {books};
            return {books:[...state.books,...action.payload]}
            break;
            case "delete_book":
            const currentBookToDelete = [...state.books];
            const indexToDelete = currentBookToDelete.findIndex(
                // (book)=>{book.id===action.payload.id;}
                function(book){
                return book.id===action.payload.id;
                }
            )
                    console.log("delete",action.payload.id);

            return {books:[...currentBookToDelete.slice(0,indexToDelete),
                ...currentBookToDelete.slice(indexToDelete+1)]}
            break;
            case "update_book":
            const currentBookToUpdate = [...state.books];
            const indexToUpdate = currentBookToUpdate.findIndex(
                // (book)=>{book.id===action.payload.id;}
                function(book){
                return book.id===action.payload.id;
                }
            );
            const bookToUpdate = {
                ...currentBookToUpdate[indexToUpdate],
                title:action.payload.title
            };
                    console.log("update",bookToUpdate);

            return {books:[...currentBookToUpdate.slice(0,indexToUpdate),bookToUpdate,
                ...currentBookToUpdate.slice(indexToUpdate+1)]}
            break;

        }
        return state;
    };
    ```

12. Separate actions and reducers: shopping cart, in one file, easy to understand, but code become hard to maintain, solution: separate into different files, use reducer.combine(),

13. Notice: when import, {}, find the obj in {} from '', without {} means import the obj which is export in '' and name it as ..

    - eg: `import  reducers  from './reducers/index';` vs. `import {addToCart} from './actions/cartActions';` name the export object in index as reducer; import addToCart, which is in cartActions.

14. Middleware(optional): implement a state logger to save state and show it pretty. we using logger,so we can remove store.subscribe method

    1. install: `npm i --save-dev redux-logger`

    2. add 

        ```
        import { applyMiddleware, createStore } from "redux";
        import logger from 'redux-logger';

        const middleware = applyMiddleware(logger);
        const store = createStore(reducers, middleware);
        ```

## 2. Create app

1. Install react : `npm i --save react`, and then`npm i --save react-dom`, and ` npm i --save react-redux`, and ` npm i --save react-router`

2. Render a class in html

    ```
    render(
        <BooksList />, document.getElementById('app')
    )
    //in class BooksList(bookList.js):
    class BooksList extends React.Component{

        render(){
            return (
                <div>
                    <h1>hi react-xy</h1>
                </div>
            )
        }
    }

    ```

3. Redux + React: it will make the redux store available in react, we need the redux component called provider, the provider wraps the entire react app and pass the store as props to react component.

4. Connect react and redux: when pass mapStateToProp as an argument to connect(), component is subscribing to the store, by doing this, returns the updated states to our local component

5. Dispatch actions: 

    1. export function in bookActions.js

    2. deal with action in bookReducer.js

    3. connect in component: bookList.js

6. Design shopping cart

    1. react-bootstrap, recommended, translate bootstrap into pure react component `$ npm install --save react-bootstrap`

7. Architecture

    - main.js

        - menu.js

        - footer.js

        - booksList.js: a list of books, bookItem.js+cart.js

        - booksForm.js

        - about.js

        - contacts.js

8. Create bookItem component

    - title, 
    
    - description

    - price

    - buy now btn









## Note

1. virtual DOM, only update the changed element.
2. babel, jsx javascript compile engine
3. redux framework, flux