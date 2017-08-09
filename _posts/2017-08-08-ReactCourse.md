---
layout: post #post
title: React Course and Build a Book Store #post title
categories: React #post category, seperated by space
tags: React Note #post tag, seperated by space
---


Udemy course


1. why redux
  - application state, store all components' state, children components get these states by this.props. children components can also have its state 
  - state container, store application states.
  - setup:
  - workflow: store(create and maintain states)-->provider(passing down store as props)-->actions(fire actions to update states)-->middleware(useful, create a kind of chain of action when the action reaches the user which evaluates what to do with the action)-->reducers(update the data in the store which then updates the app)-->store(so on in a cycle)
  - middleware: hook function
 
 2. setup 
  - install express, webpack, babel
  ```
  npm init
  npm i --save express
  npm i --save webpack
  npm i --save babel-core babel-loader babel-preset-es2015 babel-preset-stage-1 babel-preset-react
  npm i --save redux
  ```
  - design file tree:
  ```
  --AppFile
    - node_modulus(folder)
    - public(folder)
      - index.html
    - src(folder)
      - app.js
    - package.json
    - server.js
    - webpack.config.js   
  ```
 3. start. Start node and webpack, go to localhost:3000
 ```
 node server.js
 webpack
 ```
