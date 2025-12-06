---
draft: false
title: 'Life calendar widget log3'
tags: ["Resources","Insightful"]
---
## log 3:-

I was facing an error when I run my electron app which displays `object Nodelist` instead of the actual value recieved from the input of the form. It turns out that since i am using `getElementsbyName` which will return node list instead of the object

solved the error by adding index value to the nodelist
```js
const age = document.getElementsbyName('age')[0].value;
```

but when I tried to use `getElementbyId` the electron app does nothing and I need to find out why because when I use `getElementsbyName` it works as expected without errors.

So after spending some time searching for the solution to the error I was facing before I found out that the elements were fetched before the `DOMcontents` were loaded and I found out how to solve the problem
```js
document.addEventListener("DOMContentLoaded",()=>{"function to be called or values to be fetched" })
```
by using the above code you can ensure that the `DOMcontents` were loaded before the values are fetched but since the `getElementById` doesn't satisfy my needs I decided to go with `getElementsbyName` 

In order to create a life calendar which comprises of a table with lots of boxes just like a normal calendar but with functionality such as clickable and state changable etc... seems like a very big and complex task so I decided to break it down into small simpler tasks

**Task 1:-**

First I need to create a calendar with tables and there were a lot of methods and options to do so such as using `<Table>` element in html, `Pre-built templates`, `grid` and using `frameworks` etc... but we need to use one which is efficient at the same time it doesnt overkill the project so I decided to go with `gird`. If you are an experienced developer I know that you will think i made the right choice but for the starters I have to explain because they might have a doubt. so lets go through it one by one, at first we have the `<Table>` element from `HTML` this is not feasible because my calendar has more than 50 boxes and we need to create all of them manually so it is out of option. second, we have `pre-built templates` and we can use them and they are feasible but this project is all about gaining experience so, I cant use this.third, we have the `frameworks` obviously it would overkill the project because by the i spend setting up the project, I can complete it without the framework and last we have `grid` which is suitable and feasable in every way 

I learned about `grid-templates` in css by refering the web and i fouund out some of the best go-to websites to learn or revise the concepts and I will share them here for you guys
```
https://www.joshwcomeau.com/css/interactive-guide-to-grid/
```
```
https://learncssgrid.com/
```
I achieved `grid-emplate` by creating it entirely using `Javascript`. The reason i did it using Js because I dont want to create multiple `HTML` pages and make it look like a website inside a desktop widget so, I used one `HTML` page and updated it using `Js` with the help of `Eventhandling` and `Js DOM Manipulation` and I will add the code below for your reference

```js
const age=data.age;
const totalBoxes = (80-age)*52;
const rows = Math.ceil(totalBoxes/57);
const calendar = document.createElement("ul");
calendar.id="parent";
calendar.style.listStyleType="none";
calendar.style.display="grid";
calendar.style.gridTemplateColumns="repeat(57,20px)";
calendar.style.gridTemplateRows=`repeat(${rows},20px)`;
//calendar.style.gridAutoRows = "20px";
calendar.style.height="600px";
calendar.style.width = "fit-content"; // ✅ Prevents extra space
calendar.style.padding = "0";
calendar.style.gap = "0"; // ✅ No gaps
calendar.style.overflow = "hidden"; 
calendar.style.marginRight="100px";
```
P.S. I made it dynamic by creating the rows based on user's input

**Task 2:-**

Now I need to create the child elements which should contain a state and a function to make it interactive and to remeber the action made. I achieved these using Js `localstorage` and `for` loop. I know you guys will think "local storage makes sense but why for loop?". Since i made the rows dynamic it has to be created based on user input hence i have used for loop to create the child elements for the input provided by the user

```js
const savedState = JSON.parse(localStorage.getItem("lifeCalendarBoxState")) || {};
for(let i=1;i<=totalBoxes;i++){
    //box element
    const box = document.createElement("li");
    box.id=`box-${i}`;
    box.textContent="";
    box.style.aspectRatio="1/1"
    box.style.border="0.5px solid white";
    //button inside box element
    const button = document.createElement("button");
    button.id=`button-${i}`;
    button.style.border="none";
    button.style.backgroundColor="rgb(36, 36, 36)";
    button.style.width = "100%";
    button.style.height = "100%";
    button.style.border = "none";
    button.style.color = "white";
    button.style.fontSize = "10px";
    button.style.fontFamily = "monospace"; 
    button.style.cursor = "pointer";
    button.style.display = "flex";
    button.style.alignItems = "center";
    button.style.justifyContent = "center";
    button.style.boxSizing = "border-box";
    button.style.lineHeight = "1";
    button.textContent = savedState[`box-${i}`] ? "X" : "";
    button.addEventListener("click", () => {
        const key = `box-${i}`;
        if (button.textContent === "X") {
          button.textContent = "";
          delete savedState[key];
        } else {
          button.textContent = "X";
          savedState[key] = "X";
        }
        localStorage.setItem("lifeCalendarBoxState", JSON.stringify(savedState));
      });

    box.appendChild(button);
    calendar.appendChild(box);
}
```

**Task 3:-**

Now i need to create a reset button in case the user had made a mistake or has a change of mind. What can i say "we're only human, after all". And I achieved this using the same old `Javascript`

```js
const resetBtn = document.createElement("button");
resetBtn.id="button";
resetBtn.textContent = "Reset Calendar";
resetBtn.style.marginTop = "20px";
resetBtn.addEventListener("click", () => {
    localStorage.removeItem("lifeCalendarFormData");
    for (let i = 1; i <= (80 - age) * 52; i++) {
        localStorage.removeItem(`box-${i}`);
    }
    location.reload();
});
document.body.appendChild(resetBtn);
```
so far so good.now all that's left is to create the identity statement which was inspired from the `Atomic Habits` and this can be done easily because it's just plain text with some dynamic data or should i say user's input

```js
const identityLine1=data.identityLine1;
const identityLine2=data.identityLine2;
const identityLine3=data.identityLine3;
const timecommit=data.timecommit;
const timeofday=data.timeofday
const goal=data.goal;

const headingText = document.createElement("h2")
headingText.textContent=`I am the kind of person who does ${identityLine1}, because I value ${identityLine2} and want to become ${identityLine3}`

const subheadingText = document.createElement("h4")
subheadingText.textContent=`Daily System: ${timeofday}, ${goal} for ${timecommit} hour/hours`
 document.body.appendChild(headingText);
 document.body.appendChild(subheadingText);
 ```
