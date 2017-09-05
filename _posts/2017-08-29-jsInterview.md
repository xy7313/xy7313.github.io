---
layout: post #post
title: JavaScript Interview question #post title
categories: JavaScript #post category, separated by space
tags: Front-end JavaScript Interview #post tag, separated by space
---

1. what is callback function？

    1. define before invoke
    2. high order function, pass as a parameter
    3. mostly implement asychronize
    4. 

2. bind, apply&call:
    - bind function want later call

3. visibility, hidden exist dom tree/none??
4. block none, not exist

5. position: fixed, view board, screen

6. absolute, non-static parent, or screen

7. box model: order.

8. selector: .class #(hash, pound)id tagName

9. prototype, inherit

10. design pattern, singleton, module, 

11. promise

12. what is clousure, how to use, example:
 bank account deposit, withdraw, balance object, two props, a function :blanace

clousure, hide prop, do not want balance are visible 

13. scpoe lagcical 词法zuoyongyu, before browser executed code, we determine scope, each function wil have scope allocate by compiler, lookup parent chain, find nothing, return undefined 

14. use strict, 

15. 2. Javascript 各种， create object, create functions. Javascript closure (不知道)
javascript的一些exception和error detection,


1. ES6 Good Features

    1. Put the default values of parameters directly in the signature of functions; `var link = function(height = 50, color = 'red', url = 'http://azat.co') {...}`

    2. Template Literals in ES6: output variables using new syntax `${variableName}` inside of the back-ticked string rather than template literals or interpolation; 
        ```
        var url = `http://localhost:3000/api/messages/${id}`
        ```
    
    3. Multi-line strings using back-tick, too.

    4. Destructuring: retrieve prop value of an object, we can use `var {name,id} = $('student').data()` or works with arrays like:`var [col1, col2]  = $('.column'),[line1, line2, line3, , line5] = file.split('\n')`, rather than writing in two sentences like `var stu = $('student').data(), name = stu.name, id = stu.id;`. (sweet sugarcoating)

    5. Enhanced object literals: mind blowing now! In ES5, object literals is glorified version of JSON; to ES6, it becomes to something closely resembling classes.

    6. Arrow Functions

    7. Promise？？

    8. Block-scoped constructs let and const

    9. Class in ES6 has map, set object？？

    10. Modules in ES6: export import with modules

    ```
    概念讨论题：
    1. What is website accessibility and how to improve the accessibility of a website?

    2. Have you ever used any CSS preprocessors? Give the pros and cons of using CSS preprocessor.
    (谈谈CSS预处理器使用上的经验，比如SASS、LESS之类。分析一下CSS预处理器的优缺点)

    3. Tell me about event bubbling. How could you use it?

    Coding题：
    1. 预测结果：
    var Foo = function(a) {  
        function bar() {   
            console.log(a); 
        };
        this.baz = function() {
            console.log(a);
        };
    };

    Foo.prototype = {  
        biz: function() {    
            console.log(a); 
        }
    };

    var f = new Foo(7); 
    //输出结果：
    f.bar(); // result: TypeError, f.bar is not a function.  
    f.baz(); // result: 7  
    f.biz(); // result: ReferenceError, a: undefined

    2.  已知endorsement array, 要求写一个function实现想要输出的结果：
    // function input
    var endorsements = [
    { skill: 'javascript', user: 'Chad' },
    { skill: 'javascript', user: 'Bill' },
    { skill: 'javascript', user: 'Sue' },
    { skill: 'html', user: 'Sue' },
    { skill: 'css', user: 'Sue' },
    { skill: 'css', user: 'Bill' }
    ];
    // function output
    [
        { skill: 'javascript', user: [ 'Chad', 'Bill', 'Sue' ], count: 3 },
        { skill: 'css', user: [ 'Sue', 'Bill' ], count: 2 },
        { skill: 'html', user: [ 'Sue' ], count: 1 } 
    ];
    solution:
    var endorsements = [
        { skill: 'javascript', user: 'Chad' },
        { skill: 'javascript', user: 'Bill' },
        { skill: 'css', user: 'Sue' },
        { skill: 'javascript', user: 'Sue' },
        { skill: 'css', user: 'Bill' },
        { skill: 'html', user: 'Sue' }
        ];
    let after =[];
        
    endorsements.reduce((dict, item)=>{
        if(!dict[item.skill]){
        dict[item.skill] = {
            skill:item.skill,
            user:[item.user],
            count:1
            };
            after.push(dict[item.skill]);
        }else{
            dict[item.skill].user.push(item.user);
            dict[item.skill].count++;
            
        }
        return dict;
    },{});
    after = after.sort((a, b) => b.count - a.count)
    console.log(after);

    /*result:
    [
        { skill: 'javascript', user: [ 'Chad', 'Bill', 'Sue' ], count: 3 },
        { skill: 'css', user: [ 'Sue', 'Bill' ], count: 2 },
        { skill: 'html', user: [ 'Sue' ], count: 1 }
    ];
    */

    ```


#### 6 interview questions on JavaScript

1. How do you implement an extend function that takes an object & extends it with new properties and makes it work on n levels of recursion?  duplicate jquery extend

2. Write an event emitter base class that allows you to add event listeners? How would you write one that is distributed?

3. Functions as objects, how does it affect variable scope

4. What modern frameworks and utilities excite you?

5. .call() vs. .apply()  this keyword is not as predictable as any other languages that function can be applied to other objects and generally  be treated as data

6. Inheritance in javascript: JavaScript inheritance module is unique
ally as ob and 

7. Favorite feature in html5 and css3

    - html5 new elements, header footer nav, a bunch of new element, can use canvas, new element for audio and can embed video

    - css3 media query, make website responding to different devices, css3 now has animation now, css box model,

8. Describe workflow when you are creating webpage

    - First: ps mockup code page html, css, sublime/vscode(code editor) after html/css, using js, 

    - Put js at bottom, so the page load faster, imgs are optimized: load faster, minify css, delete useless whitespace, (website accessibility)

    - After finish, make sure the code to w3 standard, check project in different browser or mobile, 

9. Diff css resetting, css normalizing

    - Resetting a way when have h1 or p browser do by default give a margin, padding, resetting remove everything automatically added to elements, so you can define you own style

    - Normalizing, render htm element consistently in the same way in any browsers make sure they have the same style

10. Diff inline block, block element

    - span{display:inline;}

        - inline element does not accept any width, height attribute,

        - inline accept margin left/right, but no margin top or bottom, allow you to stylize paddings everywhere(four directions)

    - span{display:inline-block;}

        allows you to put width, height, margin ,

    - span{display:block;}
    
        accept all, take all width, full width, other element will surround it

11. explain css box model

        an example:

        content:
        padding:
        border:
        margin: 

12. What happens if two functions call each other recursively? 
    
    - The recursive calls stop after some time automatically

13. NaN, undefined

14. associative array: map, dict, key is unique 

15. Which function returns a part of an array without affecting it? slice(), not join(), concat(),splice()

16. navigator object represents  browser, document the whole dom, document object model

17. Diff var vs let vs const

    - var has been in js since the beginning; has function scope, do not respect all other blocks except function block; gets hoisted

    - let was introduced recently in ES2015; has block scope, which means a variable defined will die at the end of the block is defined scope or gc

    - const after the first assignment value, you can not assign a new value again. `const c; c = 1;` we get an error because the first declaration will assign "undefined" to c, but if c is an object, we can modify it like c.push(), add an element to c

18. Diff triple equal sign vs ==: value and data type, only value

19. NaN vs undefined

when you not define a variable, an object, js puts a placeholder: undefined, typeof(undefined) -> undefined, typeof(null) -> obuject.

20. this:

this must belong to an object,

non strict, function is window, this-->window
strict

this.bind copy code from original function, this point to first para in bind, call/apply, call immediatly


21. NaN number, 

22. IIFE, all variables inside are local variables, it will not be changed by outside operations and will not mess up global variables.

23. require是在React部分问的，所以答AMD是对的，因为AMD（异步加载，异步执行）是浏览器端目前的模块规范，如果是Nodejs，应该回答CommonJS（同步加载，同步执行）。如果问最新规范或者ES6推荐规范，应该回答CMD（异步加载，同步执行）

24. Angular
AngularJS is a toolset for building the framework most suited to your application development. It is fully extensible and works well with other libraries. Every feature can be modified or replaced to suit your unique development workflow and feature needs.







JavaScript
1. What is the significance of, and reason for, wrapping the entire content of a JavaScript source file in a function block?
1. This is an increasingly common practice, many JS libraries have adopted this. This technique creates a closure
     around the entire JS file, this helps to avoid the clashes between different JS modules and libraries.
2. This technique allows an easily referenceable alias for a global variable. It's most common in jQuery plugins,
     used $ to reference jQuery.
(function($){})(jQuery)
 
2: What is callbacks?
A callback function is a function that is
1) passed as parameters to another function, and
2) will be invoked after some kind of events.
A callback function is a function you provide to another piece of code, allowing it to be called by that code.
 
2. What is the advantages of including 'use strict' at the beginning of JS file?
1. Compile time check. Means when you are writing your code, you can easily correct your typos or duplicate
declarations.
2. Eliminates this coercion, prevent accidental globals. like a= 4
 
3. What is closure in JS?
1. A closure is an inner function that has access to the outer function even the outer function has closed.
2. It provides different methods that could get the data from the parent object scope and return with wantted way.
 
4. What are the advantages of using JavaScript?
1. Less server interaction, improve performance
2. Immediate feedback to visitors
3. Increase interactivity with users
4. Build dynamic User interfaces
 
5.  Why Javascript is asynchronous.
1. Javascript is almost all I/O non-blocking, this could be concluded as Web Api's, Calls such as Ajax, SetTimeOut,
    Events etc.
2. CallBack Queue: All the async callback functions or events like onclick are pushed to this queue.
3. Event loop. There is always one function to look in the stack and queue and if the stack is empty, push the contents
    from callback queue to the stack.
 
6. What is scope chain, hoisting.
Hoisting is Javascript's default behavior of moving the variable and function declarations to the top.
Scope chain: When a variable is used, the program traverses the scope chain until it finds an entry for that variable. Redeclaring a variable or passing it into a function is a way of separating it from its previous existence in the scope chain.
 
7. Difference between class inheritance and prototype inheritance?
Class inheritance: instances inherit from classes, sub-class relationships. It's a kind of creating tight coupling or hierarchies.
Prototypes:  instances inheirt directly from other objects. Instances are typically instantiated via 'Object.create()'.
    Instances may be composed from many different objects, allowing for easy selective inheritance.
 
8. Pros and cons of OOP and FP?
OOP Pros: Modularity for easier troubleshooing, Reuse of code through inheritance, flexibility through polymorphism and
      effective problem solving.
         cons: Too many relationships to handle, OOP depends on shared state. Lead to undesirable behavior such as race conditions
FP pros: Avoid any shared state or side-effects, eliminates the race conditions for the same resources.
               Instead of concentrate on what to do, letting the underlying functions take care of the how. This leaves tremendous latitude
      for refactoring and performance optimization.
FP Cons: Over exploitation of FP features such as point-free style and large compositions can potentially reduce readability because the resulting code is often more abstractly specified, more terse, and less concrete.
 
9. What is this, how to change the ownership of this?
This refers to the object that owns this code.
The value of this is determined by how a function is called.
There are two ways to manually set this value. They are .apply() and .call() .
.apply and .call have very small difference.
For both of them, the first argument must be this, and the second parameter for .apply is [], but .call can accept any arguments.
 
10. Bind vs Call vs Appliy?
https://stackoverflow.com/questions/15455009/javascript-call-apply-vs-bind
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind
Use .bind() when you want that function to later be called with a certain context, useful in events, and bind() function creates a new bound
function(BF), that wraps the original function object.
Use .call() or .apply() when you want to invoke the function immediately, and modify this value.
For bind(), we use it primarily to call a funtion with this value set explicitly. Bind() allows us to easily set which specific object will be bound
to this when a function or method is invoked.
 
11. What is event bubbling?
Event bubbling directs an event to its intended target, it works like this
1. a button is clicked and the event is directed to the button
2. if an event handler is set for that object, the event is triggered
3. if no event handler is set for that object, the event bubbles up to the objects parent
And event bubbles up from parent to parent until it is handled or it reaches the document object.
 
12. Good features of ES6.
https://webapplog.com/es6/
Default Parameters in ES6 :  var height = height || 50;
Template Literals in ES6: ${syntax} in back stick expression
Multi-line Strings in ES6
Destructuring Assignment in ES6
Enhanced Object Literals in ES6
Arrow Functions in ES6
Promises in ES6
Block-Scoped Constructs Let and Const
Classes in ES6, has Map, Set object
Modules in ES6: export import with modules
 
13. What is controlled & uncontrolled component?
Controlled component is a component where React is in control and is the single source of truth for the form data.
Uncontrolled component is where your form data is handled by the DOM, instead of inside your React component.
 
14. Javascript inheritance?
Javascript has only one construct: object. Each object has a private property (prototype) which holds a link to another object called its prototype.
And that prototype object has its own prototype, and so on until an object reached null as its prototype. Also null is the final link in the prototyp
chain.
 
15. What is promise?
Promise is a JavaScript object used to handle asynchronized operations, and the result would be get in the future.
To avoid loop hell, nested functions
It has 3 states: pending, fullfilled, rejected.
A common need is excute 2 or more asynchronous operations, where each subsequent  operation starts when the previous operation succeeds,
with the result from previous step. We accomplish this by creating a promise chain instead of two many nested functions.
doSomething(function(result) {
  doSomethingElse(result, function(newResult) {
    doThirdThing(newResult, function(finalResult) {
      console.log('Got the final result: ' + finalResult);
    }, failureCallback);
  }, failureCallback);
}, failureCallback);
-------------------------------------------------------------------------
doSomething().then(function(result) {
  return doSomethingElse(result);
})
.then(function(newResult) {
  return doThirdThing(newResult);
})
.then(function(finalResult) {
  console.log('Got the final result: ' + finalResult);
})
.catch(failureCallback);
From <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises>
 
16. What is map and reduce?
The map() method creates a new array with the results of calling a provided function on every element in the calling array.
The reduce() method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.
 
17. What is curry and compose?
First, currying is translating a function that takes multiple arguments into a sequence of functions, each accepting one argument.
Notice the distinct way in which a curried function is applied, one argument at a time.
Second, function composition is the combination of two functions into one, that when applied, returns the result of the chained functions.
It's very common practise in React, ex. React middle ware, that uses enhancer to compose a list of middle ware, and works like a work flow to pass the states.
The two concepts are closely related as they play well with one another.



1. cookie: all browser information in client side
local storage and session storage. session-temp； local-permanent



//more code in interview-xy