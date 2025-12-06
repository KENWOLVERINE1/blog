---
draft: false
title: 'Life calendar widget log2'
---
## log 2:-

## Configuring UI(User Interface):-

1. The User Interface in electron works just like any other websites but in a more traditional way. we need to create a browser window in order to view our UI.for that we can use `BrowserWindow` from electron.

Create your `index.html` based on your preferences or you can use my `index.html` which i have created for the `life-calendar-widget`.This project requires you to answer few questions which was made by referencing and combining various concepts and techniques which we will discuss in detail later in the upcoming logs

>**Note**: You can use `React` or any other `Frameworks` to create your `UI` because electron uses `Nodejs` so, it supports everything that can be used by `Node`

Rigth now I will give you an overview of the concepts that are used to create this project. I have used the `Memento Mori Framework`,`identity based habits` from `atomic habits` and `daily system goals` as the base logic for this project

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Life Calendar Widget</title>
</head>
<body>
    <center><h1>Life Calendar Widget</h1></center>
    <hr/>
    <br/>
    <!--<div id="display"></div>-->
    <p id="display"></p>
    <h2 id="h2">Answer the questions asked below to get your life calender <3</h2>
    <br/>
    <br/>
    <form id="form">
      <label for="age">1. Enter your Age</label><br/>
      <input type="number" id="age" name="age"><br/>
      <br/>
      <label for="identityLine">2. Let's create your identity line</label><br/>
      <label for="identityLine1">I am the kind of person who<input type="text" id="identityLine1" name="identityLine1"></label><br/>
      <label for="identityLine2">Because I value<input type="text" id="identityLine2" name="identityLine2"/></label>
      <label for="identityLine3">want to become <input type="text" id="identityLine3" name="identityLine3"/></label><br/>
      <br/>
      <label for="timeofday">3. What time of day are you sharpest(mornign/afternoon/evening)?</label><br/>
      <input type="text" id="timeofday" name="timeofday"/><br/>
      <br/>
      <label for="goal">4. What is your #1 goal right now (e.g.build a business,get fit,learn a skill)?</label><br/>
      <input type="text" id="goal" name="goal"/><br/>
      <br/>
      <label for="timecommit">5. How much time can you commit daily (Even 1 hour is enough)</label><br/>
      <input type="number" id="timecommit" name="timecommit"/>
      <br/>
      <br/>
    </form>
    <center><button onclick="lifechartdisplay()" id="button" type="submit">Get Calendar</button></center>
    <link href="index.css" rel="stylesheet"/>
    <script src="./renderer.js"></script>
  </body>
</html>
```

>**Note**: The `style sheet(CSS)` is required to achieve the exact result that is provided by the life-calendar-widget App or you can use `Bootstrap`,`SCSS `,`SASS` or `TailwindCSS` based on your preference

2. In order to display the UI we need to configure `main.js`.first we need to import the required modules from electron
```js
import { app, BrowserWindow } = require("electron")
```

next we need to create a `BrowserWindow` for our App
```js
const createWindow=()=>{
    const win= BrowserWindow({
    width:850,
    height:850,
    maxWidth:850,
    maxHeight:850,
    minWidth:450,
    minHeigth:500
})
win.loadFile("index.html)
}
```

Once our `BrowserWindow` is ready we need to call the `createWindow` function to implement it
```js
app.whenReady().then((=>{
    createWindow()
}))
```

These are the basic configurations that we need to run the electron app in our desktop

3. Since I am using Traditional web development methods I need to create a `Javascript` file for the functionality of the App
```sh
touch renderer.js
```

The name of the file can be anything according to your preferences but the logic file is named as `renderer.js` in the electron `docs` so i am following the same
