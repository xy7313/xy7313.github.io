---
layout: post #post
title: JavaScript More functions and operating DOM #post title
categories: JavaScript #post category, separated by space
tags: Front-end JavaScript #post tag, separated by space
---



## Notes
18. promise
    ```
    var fn = function(){
      setTimeout(function(){
        return 'called';
      },3000);
    };

    var resp = fn();

    document.write(resp);
    //output: undefined
    ```

    ```
    var fn = function(){
      var promise = new Promise(function(resolve,reject){
        setTimeout(function(){
            //resolve('called');
            reject('err');
            
          },3000);
      });
      return promise;
    };

    var resp = fn();

    document.write(resp);

    resp.then(function(data){
      document.write(data);
    },
    function(err){
      document.write(err);
    });
    ```

19. closure: inner function can access outer function variable.

    ```
    //before:
    var fn = function(){
      var cntr = 0;
      var inc = function(){
        cntr++;
        return cntr;
      };
      return inc();
    };

    var resp = fn();

    document.write(fn()+'<br/ >');
    document.write(fn()+'<br/ >');
    document.write(fn()+'<br/ >');
    output:1,1,1
    ```

    ```
    //after
    var fn = function(){
      var cntr = 0;
      var inc = function(){
        cntr++;
        return cntr;
      };
      return inc;
    };

    var resp = fn();

    document.write(resp()+'<br/ >');
    document.write(resp()+'<br/ >');
    document.write(resp()+'<br/ >');
    //output: 1,2,3
    ```

    ```
    //return more than one func
    var fn = function(){
      var cntr = 0;
      
      var inc = function(){
        cntr++;
        return cntr;
      };
      
      var reset = function(){
        return cntr=0;
      };
      
      return {
        'inc':inc,
        'reset':reset
      };
    };

    var resp = fn();
    document.write(resp.inc()+'<br/ >');
    document.write(resp.inc()+'<br/ >');
    document.write(resp.inc()+'<br/ >');
    ```

    ```
    //a funny example
    function abc(a){
      return function(b){
        console.log("a+b",a+b);
        return function(c){
          console.log("all:",a,b,c);
          return a+b+c;
        }
      }
    }

    console.log("final:",abc(2)(3)(4));
    ```

20. js operate html

    ```
    //js manipulate dom, js should load after html, at the buttom of html
    //or use this onload function in the top of js file to make sure the js code is executed

    window.onload = function(){
      var elem = document.getElementById('div');
      elem.innerHTML = 'div3';
      
      var elems = document.getElementsByTagName('div');
      elems[0].innerHTML = 'div1';
      
      //retrieve custom attribute using query selector
      var elem4 = document.querySelector('div[username="4"]');
      elem4.innerHTML = '4~';
    }
    ```

21. js event handling

    ```
    window.onload = function(){
      document.getElementById('btn').onclick = function(){
        alert('hi');
      };
    }
    ```

    ```
    //change div content using input text
    window.onload = function(){
      document.getElementById('btn').onclick = function(){
        alert('hi');
        var content = document.getElementById("txtbx").value;
        document.getElementById('div').innerHTML = content;
      };
    };
    ```

    ```
    window.onload = function(){
      document.getElementById('btn').onclick = function(){
      var newContent = '<h2>hi</h2>';
      //beforebegin
      //afterbegin
      //beforeend end of the element content
      //afterend
      document.getElementById('div').insertAdjacentHTML('beforeend',newContent);
      };
    };
    ```

22. event listener

    ```
    //two kinds: element listener, event listener
    window.onload = function(){
      document.getElementById('btn').addEventListener('click',function(){
        alert('hi');
      });
    };
    ```

    ```
    window.onload = function(){
      function eventFn(){
        alert('hi');
      }
      document.getElementById('btn').addEventListener('click',eventFn);
      document.getElementById('btn2').addEventListener('click',function(){
        document.getElementById('btn').removeEventListener('click',eventFn);
      });
    };
    //click: alert, remove->click: no alert
    ```

## A practice - shift input to output box and keep the order
- script.js

    ```
    window.onload = function(){
      var interval_var ;

      function shift(direction,time){
        var leftElem = document.getElementById("input");
        var rightElem = document.getElementById("output");
        window.clearInterval(interval_var);
        interval_var = setInterval(function(){
          var leftStr = leftElem.value;
          var rightStr = rightElem.value;
          console.log(leftStr);
          if(direction == "toRight") {
            rightElem.value =  leftStr.substring(leftStr.length-1,leftStr.length)+rightStr;
            leftElem.value = leftStr.substring(0,leftStr.length-1);
            console.log("right",rightElem.value);
            if(leftElem.value.length===0){
              clearInterval(interval_var);
            }
          }
          if(direction == "toLeft") {
            rightElem.value = rightStr.substring(1,rightStr.length);
            leftElem.value = leftStr+rightStr.substring(0,1) ;
            console.log("left",leftElem.value);
            if(rightElem.value.length===0){
              clearInterval(interval_var);
            }
          }
        },time);
      }
    
      document.getElementById("btn1").addEventListener('click',function(){
        shift("toRight",1000);
      });
      document.getElementById("btn3").addEventListener('click',function(){
        shift("toLeft",1000);
      });
      document.getElementById("btn2").addEventListener('click',function(){
        clearInterval(interval_var);
      });
    };
    ```

  - html:
    ```
    <body>
        <h1>Hello Plunker!</h1>
        <div id = "div">
          shift
        </div>
        <br/> 
        <input type="text" id = "input" value = "default"/>
        <input type="text" id = "output"/><br/>
        <input type="button"  id="btn1" value=">>" />
        <input type="button"  id="btn2" value="||" />
        <input type="button"  id="btn3" value="<<" /> 
      </body>
    ```

