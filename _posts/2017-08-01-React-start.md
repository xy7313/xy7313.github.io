---
layout: post #post
title: React prologue #post title
categories: React #post category, seperated by space
tags: React Note #post tag, seperated by space
---

[tutorial video](https://www.youtube.com/watch?v=-AbaV3nrw6E&list=PL6gx4Cwl9DGBuKtLgPR_zWYnrwv-JllpA&index=1)

1. Download code:  https://github.com/buckyroberts/React-Boilerplate, My editon with notes: https://github.com/xy7313/React-Boilerplate

2. Include JSX 
```
//after download, also can ref online file,
<script src="../../js/react.min.js"></script>
<script src="../../js/react-dom.min.js"></script>
<script src="../../js/browser.min.js"></script>
```

The last line transpile jsx file to plain js file so that browser can understand jsx. There are also some online tools can do the same work for developer.
 - an example:
 ```
 <!DOCTYPE html>
<html>

  <head>
    <script data-require="react@*" data-semver="15.5.0" src="https://cdnjs.cloudflare.com/ajax/libs/react/15.5.0/react.min.js"></script>
    <script data-require="react@*" data-semver="15.5.0" src="https://cdnjs.cloudflare.com/ajax/libs/react/15.5.0/react-dom.min.js"></script>
    <script data-require="react@*" data-semver="15.5.0" src="    https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.24/browser.min.js"></script>
    <link rel="stylesheet" href="style.css" />
  </head>

  <body>

    <div id="container"></div>

    <script type="text/babel">
        ReactDOM.render(
            <h2>Welcome to React!</h2>,
            document.getElementById('container')
        );
    </script>

  <script src="script.js"></script>
  </body>

</html>


 ```
 

3. Include bable: we add a h2 tag into the html element whoes id is 'container'
```
 <script type="text/babel">
        ReactDOM.render(
            <h2>Welcome to React!</h2>,
            document.getElementById('container')
        );
</script>
```

4. Components parts of your website, entire application is made up of components.

5. Super component:
```
<script type="text/babel">
    var BuckysComponent = React.createClass({
        //object
        //return html
        render: function() {
            return (<h2>This is a simple component</h2>);
        }
    });
    ReactDOM.render(<BuckysComponent />, document.getElementById('container'));
</script>
```

6. Mutiple components
 - One component can only return one parent element(div). The render `ReactDOM.render(..,..)`can only render only one one parent tag
 - when we want to return more than one html tags.
 ```
 <script type="text/babel">
    var BuckysComponent = React.createClass({
        //object
        //return html
        render: function() {
            return (
               <div>
                   <h2>This is a simple component</h2>
                   <p>para</p>
               </div>
           );   
        }
    });
    ReactDOM.render(<div>
                     <BuckysComponent />
                     <BuckysComponent />
                 </div>, document.getElementById('container'));
</script>
```

 7. Properties: make template for one component and customize in different ways. Using curly brace{}
  - Property is essentially an HTML attribute that we can pass in to customize our components in different kinds of ways.
 ```
<body>
    
    <div id="container"></div>

    <script type="text/babel">
      var Movie = React.createClass({ 
        render:function(){
          return(
                  <div>
                    <h1>{this.props.title}</h1>
                    <h2>{this.props.genre}</h2>
                  </div>
            );
        }
      });
        ReactDOM.render(
          <div>
            <Movie title="Avatar" genre="action"/>
            <Movie title="The NoteBook" genre="romance"/>
            <Movie title="Cube" genre="thriller"/>
          </div>,document.getElementById('container')
        );
    </script>

  </body>
//output: Avatar, action, The NoteBook, romance, Cube, thriller
 ```

8. Event handling
 - built a sticky note app, where users can add new notes, delete or edit notes and write any notes.
  - can not use class as prop's name, because class is one of the reserve words in js
  - children property(built-in prop), between the opening tag and closing tag, like: ` <Comment>hey-sample txt</Comment>`
```
<!DOCTYPE html>
<html>

 <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>React-stickyNote</title>
    <script src="../../js/react.min.js"></script>
    <script src="../../js/react-dom.min.js"></script>
    <script src="../../js/browser.min.js"></script>
    <link rel = "stylesheet" type="text/css" href = "../../css/main.css">
  </head>

  <body>
    
    <div id="container"></div>

    <script type="text/babel">
      var Comment = React.createClass({ 
        edit: function(){
          alert("edit");
        },
        remove: function(){
          alert("remove");
        },
        render: function(){
          return(
            //can not use class, because class is reserve word in js
             //children property, between the opening tag and closing tag
                  <div className = "commentContainer">
                    <div className = "commentText"> {this.props.children} </div>
                    <button  onClick={this.edit} className = "button-primary">Edit</button>
                    <button onClick={this.remove} className = "button-danger" >Remove</button>
                  </div>
            );
        }
      });
        ReactDOM.render(
          <div className = "board">
            <Comment>hey-sample txt</Comment>
            <Comment>beans</Comment>
            <Comment>TUNA txt</Comment>
          </div>,document.getElementById('container')
        );
    </script>

  </body>

</html>
```

9. State











































