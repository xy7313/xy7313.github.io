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

3. visibility hidden exist dom tree
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

