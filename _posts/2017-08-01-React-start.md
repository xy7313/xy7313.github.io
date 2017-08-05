---
layout: post #post
title: React prologue #post title
categories: React #post category, seperated by space
tags: React Note #post tag, seperated by space
---

[tutorial video](https://www.youtube.com/watch?v=-AbaV3nrw6E&list=PL6gx4Cwl9DGBuKtLgPR_zWYnrwv-JllpA&index=1)

1. download code:  https://github.com/buckyroberts/React-Boilerplate
2. include 
```
//after download, also can ref online file
<script src="../../js/react.min.js"></script>
<script src="../../js/react-dom.min.js"></script>
<script src="../../js/browser.min.js"></script>
```
The last line transpile jsx file to plain js file so that browser can understand jsx. There are also some online tools can do the same work for developer.

3. include bable: we add a h2 tag into the html element whoes id is 'container'
```
 <script type="text/babel">
        ReactDOM.render(
            <h2>Welcome to React!</h2>,
            document.getElementById('container')
        );
</script>
```

4. components parts of your website, entire application is made up of components.

5. super component:
```
var Bacon = React.createClass({
  //object
  //return html
  render: function(){
    return
  }
});
```
