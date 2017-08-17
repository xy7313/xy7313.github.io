---
layout: post #post
title: React prologue and Build a note app #post title
categories: React #post category, seperated by space
tags: React Note #post tag, seperated by space
---

[tutorial video](https://www.youtube.com/watch?v=-AbaV3nrw6E&list=PL6gx4Cwl9DGBuKtLgPR_zWYnrwv-JllpA&index=1)

1. Download code:  https://github.com/buckyroberts/React-Boilerplate, My editon with notes: https://github.com/xy7313/React-Boilerplate. Final note app click [here](https://react-note-xy.herokuapp.com), application code [here](https://github.com/xy7313/ReactNoteApp)

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

7. Properties:
 - make template for one component and customize in different ways. Using curly brace{}
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
 - Example: Built a sticky note app, where users can add new notes, delete or edit notes and write any notes.
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
 - Customize the components using properties and states. Whenever something is gonna stay the same uses properties, whenever changes uses states.
 - You don't need to explicitly say whenever your state changes to redraw a certain part of your webpage, it automatically watches for your states. Whenever their state changes, the part of web page gets redrawn automatically to fit that. 
 
   ```
   <body>

      <div id="container"></div>

      <script type="text/babel">

        var CheckBox = React.createClass({ 

          getInitialState: function(){
              return {checked:true}
          },
          handleChecked: function(){
              this.setState({checked:!this.state.checked})
          },
          render: function(){
              var msg;
              if(this.state.checked){
                  msg='checked'
              }else{
                  msg='unchecked'
              }

             return(
                     <div className = "commentContainer">
                       <input type = "checkbox" defaultChecked={this.state.checked} onChange = {this.handleChecked}/>
                       <h3>checkBox is {msg}</h3> 
                     </div>
               );
          }
        });
          ReactDOM.render(
            <CheckBox />,document.getElementById('container')
          );
      </script>

    </body>
   ```

10. Add state to component(contd on the sticky note app)
 - Requirements: This note switches bewteen two modes/states: editing, normal. That is, whenever we click edit, the text area can be changed to a form for editing. After complish editing, the form turns to text area. 
 
    ```
     <body>

       <div id="container"></div>

       <script type="text/babel">
         var Comment = React.createClass({ 
           getInitialState: function(){
             return {editing: false}
           },
           edit: function(){
             this.setState({editing:true});
           },
           save: function(){
             this.setState({editing:false});
           },
           remove: function(){
             alert("remove");
           },

           renderForm: function(){
             return(
                     <div className = "commentContainer">
                      <textarea defaultValue = {this.props.children}></textarea>
                       <button onClick={this.save} className = "button-success" >Save</button>
                     </div>
               );
           },
           renderNormal: function(){
             return(
                     <div className = "commentContainer">
                       <div className = "commentText"> {this.props.children} </div>
                       <button  onClick={this.edit} className = "button-primary">Edit</button>
                       <button onClick={this.remove} className = "button-danger" >Remove</button>
                     </div>
               );
           },
           render: function(){
             if(this.state.editing){
               return this.renderForm();
             }else{
               return this.renderNormal();
             }
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
    ```

11. refs (contd on the sticky note app)
 - Requirements: Save whatever the textarer looks like now.
 - First, get the text just typed
 - Second, show it 
 - eg: `var val = this.refs.newText.value;` + `<textarea ref = "newText" defaultValue = {this.props.children}></textarea>`

12. rearrange multiple independent components -- set up a 'parent' container (contd on the sticky note app)
 - In the note example, we define a borad, which is like a magener of all note components
 - unique identifier, key is the way to uniquely identify each child by giving an ID 
 ```
 //add Board in script babel, change ReactDom.render
 var Board = React.createClass({
        getInitialState: function(){
          return {
            comments:[
                    'I like bacon',
                    'want some ice cream',
                    'done here'

            ]
          };
        },
        render: function(){
          return (
             <div className = "board">
              {
              //anonymous  function, a.k.a a function with no name, key-unique identifier
                this.state.comments.map(function(text,i){
                  return (<Comment key = {i}>{text}</Comment>);
                })
              }
            </div>
          );
        }
      });

        ReactDOM.render(<Board/> ,document.getElementById('container')
        );
 ```
 
13. Updating state and remove notes(contd on the sticky note app)
 - clean up the render function
 - array.splice(index,num); remove num elements from index of array
 ```
 //all in var Board
 removeComment: function(i){
     console.log("remove:"+i);
     var arr = this.state.comments;
     arr.splice(i,1);
     this.setState({comments:arr});
   },
   updateComment: function(newText,i){
     console.log("new text:"+newText);
     var arr = this.state.comments;
     arr[i] = newText;
     this.setState({comments:arr});
   },
   eachComment: function(text,i){
     // unique identifier, i: increment for the array
     return (<Comment key = {i} index = {i}>
               {text}
             </Comment>);
   },
   render: function(){
     return (
        <div className = "board">
         {this.state.comments.map(this.eachComment)}
       </div>
     );
   }
 ```
  
14. Passing functions as props (contd on the sticky note app)
 - how to call functions from entirely different components? using props

15. Add new component (contd on the sticky note app)


16. Js can not figure out the scope, so we need to call band : `<button className = "button-info create" onClick = {this.addComment.bind(null,'Type here')}>New A Comment</button>`. 
 Notice that: Don't .bind in the render() function - that creates a new function every time render is called (which will be often.) .bind in the component constructor. We will create too many comment components and get an error.




































