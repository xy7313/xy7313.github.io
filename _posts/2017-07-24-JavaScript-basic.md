---
layout: post #post
title: JavaScript Basic Concept #post title
categories: JavaScript #post category, separated by space
tags: Front-end JavaScript #post tag, separated by space
---

#### 0. Webpage

1. Mostly used framework to implement responsive page layout: Bootstrap, now we have Bootstrap4

2. Html5: specify the doc type. HTML become HTML5: Put this on the top of html file`<!DOCTYPE html>`

3. **input element** can have many attributions:
    1. type, includes: date, email, password etc and text by default
    4. id of tag, unique identifier
    5. value  
    6. name 
    7. title 
    8. any custom attributions like location, organization
4. Local storage, Cookie session storage
    - Cookie: all browser information in client side
    - Local storage and session storage. session-temp； local-permanent
6. CSS file reference should be on the top of page, javascript can be at bottom. better user experience, may need more loading time,
7. Dynamic page, we need js
8. Loosely-typed language: assign data type automatically


#### 1. Object

1. Objects are containers for named value.
2. Object defination
    - Most simplest way: `var user = {“name”:xy", “age”:18};`
    - Using new keyword: `var user = new Object(); user.name = "xy";`
    - Using object constructor: `function user(name, age, phone) { this.name = name; ...} `, `var user1 = new user("xy"...);`
    - Notice here: If you try to call the user() without the new keyword. It returns *undefined*, because the user() is not returning anything, previously it was the new keywords which was returning you the object.
3. Objects are addressed by reference. See an example:`var user = {“name”: “xy”, “age”:18}; var user1 = user;`  User1 is not a copy of user, it is the user itself, so any changes to user1 will reflect user.
4. Object Properties
5. Create object: 
```
var userObj = {
    "username":"xy";
    "place":"nj";
};
userObj.addr = "Chi";
for(key in userObj){
    //output
    document.write(userObj[key]);
}
document.write(userObj.place);
```


#### 2. Object Properties
1. `var name = user.name;`
2. `var name = user[“name”]`
3. `for (key in user) { alert(key + “ ”+ user[key]); }`
4. `delete user.name;` //remove name property from user object
5.  functions as prop:
    ```
    var user = { 
        “firstname” : “xx”, 
        “lastname” : "yy", 
        “fullname” : function () { 
            return this.firstname + “ “+this.lastname;
            } 
    }  
    user.fullname(); 
    ```
6.  Create function
    ```
    function display(username="xy", place="nj"){
        return username+','+place;
    }
    document.write(display());
    document.write(display("xy1","ny"));
    ```

    ```
    //anonymous function
    function(){
        return 'anonymous function';
    }
    ```

    ```
    var fn = function(){
        return 'anonymous function';
    }
    document.write(fn());
    //output anonymous function
    document.write(fn);
    //output all function body

    //anonymous function Can be passed as parameter to another function
    function display(fnName){
        return fnName;
    }
    document.write(display(fn()));
    //output anonymous function
    ```

    ```
    //Self invoking function
    (fn = function(){
        return 'anonymous function';
    })();
    ```

    ```
    function user(){
    return {
        "username":"xy",
        "place":"nj",
    };
    }
    document.write(user().place);
    ```

    ```
    function abc(){
    var username = "xy",
        place = "nj";
        var display = function(){
            return username +","+ place;
        }
        return display;
    }

    document.write(abc()());

    //or
    var fn = abc();
    document.write(fn());
    ```

#### 3. Prototype
1. Every JavaScript function has a prototype property
2. Primarily for inheritance
3. Methods and properties added to function’s prototype property will be available to all instances of that function
4. An example: `var user = new Object();` user Inherit from the Object.prototype.
5. Adding new properties to existing prototype: `user.prototype.fullname = function() { return this.firstname + “,“+this.lastname};`
6. We want define arr.display();

    ```
    var arr = ['ar',"br","cr"];
    Array.prototype.display = function(){
    //display array
    console.log(this);
    return this.concat(this);
    }

    arr.display();

    console.log(arr.display());
    //display arr twice in a array: ["ar", "br", "cr", "ar", "br", "cr"]
    ```

#### 4. Math
1. Math.min()/Math.max()
2. Math.round(4.5) //output:5, round to the nearest integer value
3. Math.ceil(); //round up
4. Math.floor() //round down

#### 5. Array
1. Arrays are also special type of objects, Arrays uses numbered indexes and object uses named indexes
2. arr.length
3. arr.push();
4. arr[arr.length]="aa";
5. arr.shift() //remove the first element of an array
6. arr.pop() //remove the last element of an array
7. delete arr[1];
8. arr.splice(2,1); //from index 2. remove 1 element
9. arr.splice(arr.indexOf("aElement"));

#### 6. String
1. Can use single / double quotes to enclose the string.
2. str.length
3. escape the string, eg: `var username = “argopan\”kumar”;`
4. `str.indexOf("oneElement");`
5. `test_str.match(“ar”) ` //Used to find an occurrence of a substring in a string.
6. Both indexOf and match are case sensitive
7. `str.toUpperCase(); /str.toLowerCase();`
8. `str.replace(new RegExp(',', 'g'), ''); `, `str.replace(‘username’, 'ar);`
9. `str.substring(0,5);`

#### 7. Date
2. `var date_str = new Date();`//Created using new Date();
2. `date_str.getFullYear();` // return current year
3. `date_str.setFullYear(2010)` // set year
4. `date_str.getDay();` // return current day 
5. `data_str.setDate(10);`
6. `date_str.setDate(date_str.getDate() + 2);` //Adding 2 days to the current day
7. `date_str.setFullYear(date_str.getFullYear() + 2);` //Adding 2 years to the current year

#### 8. HTML DOM(document object model)
1. getElementById, document.getElementsByTagName, getElementsByClassName
2. Changing content: .innerHTML
3. Changing Attributes: .className
4. Changing Style: .style
5. Event binding: onclick
6. EventListeners: `document.getElementById("‘my_div’").addEventListener(“click”, test_fn);`, `removeEventListener(“click”, test_fn);`
7. `window.onload = function(){...}` make sure to load DOM element first
8. Popup boxes: alert, confirm box, prompt box


#### 9. Timeout
17. timeout, interval
    ```
    setTimeout(function(){
    document.write('hello');
    },1000);
    ```

    ```
    setInterval(function(){
    document.write('hello');
    },1000);
    ```

    ```
    var interval_var = setInterval(function(){
    document.write('hello');
    },1000);

    setTimeout(function(){
    clearInterval(interval_var);
    },5000);
    ```

####10. Arguments
4. arguments, 

    ```
    function(){
        //return:["ar", "br", "cr", callee: ƒ, Symbol(Symbol.iterator): ƒ]
        console.log(arguments);
        //return a slice: ["ar", "br", "cr"]
        console.log(Array.prototype.slice.call(arguments));
    }
    abc('ar',"br","cr");
    ```

#### 11. promise
[doc here] very helpful.(https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

1. 
```
let promise = doSomething(); 
promise.then(successCallback, failureCallback);
//or
doSomething().then(successCallback failureCallback);
```

2. 
```
doSomething()
.then(result => doSomethingElse(result))
.then(newResult => doThirdThing(newResult))
.then(finalResult => {
  console.log(`Got the final result: ${finalResult}`);
})
.catch(failureCallback);
```

3. 
```
let myFirstPromise = new Promise((resolve, reject) => {
     setTimeout(function(){
    resolve("Success!"); // Yay! Everything went well!
  }, 250);
});
myFirstPromise.then((successMessage) => {
  console.log("Yay! " + successMessage);
}, failureCallback);
```


4. 

    ```
    function abc(){
    var promise = new Promise(function(resolve,reject){
        setTimeout(function(){
        resolve('display');
        //reject(some http err, maybe)
        },3000);
    });
    return promise;
    }

    var resp = abc();
    //first func handles resolve, second handles reject
    resp.then(function(data){
    console.log("data,"+data);
    },
    function(err){
    console.log(err);
    })
    ```

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

#### 12. closure: inner function can access outer function variable.

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

#### 13. js operate html

1. dom props
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



