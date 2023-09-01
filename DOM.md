------------------------
# Title: How can we build webpages from javascript? By DOM! (Document Object Model).
-------------------------------------
# Note: Everything on the webpage is inside the javascript object called `document` and it is inside the object called `window`. `document` has alot of builtin functions. We can use these functions to change our HTML using DOM.

![The HTML DOM Tree of Objects](https://www.w3schools.com/js/pic_htmltree.gif "The HTML DOM Tree of Objects")
-------------------------------------
# 1) `document.getElementById("IDName");`
## This function will take a string argument and check the whole webpage if some id matches the given string and returns it for example:
```javascript
let signInButton = document.getElementById("signInButton");
```
# 2) `.addEventListener`
## This function is a part of an HTML element. So it means we can call it by something like this:
```javascript
document.getElementById("signInButton").addEvventListener("click",function(event){})
//OR:
let signInButton = document.getElementById("signInButton");
signInButton.addEvventListener("click",function(event){});
```
## `.addEventListener("Action",function(event))` takes 2 arguments. First is a string where we tell it what kind of event should it listen to. Second is a function which itself takes an argument called `event`. If the event that it is listening to occurs then perform what ever the second argument function says to do so for example:
```javascript
signInButton.addEventListener("click", function () {
	console.log("Welcome!")})
// OR:
let Welcome = () => {console.log("Welcome")};
signInButton.addEventListener("click", Welcome);
```
# 3) `document.createElement("ElementName");`
## This function takes a string argument. The String argument should match with anyone of HTML tags available. if it matches then it will return and create that element for example:
```javascript
let newli = document.createElement("li");
```
# 4) `document.createTextNode("String")`
## This function takes a string argument and creates a node with that string:
```javascript
let Yo = document.createTextNode("Yo!");
```
# 5) `.appendChild()`;
## This function is a part of an HTML element. It takes one argument which should be an HTML element. The above diagram shows what element can have what child. `li` cannot have a child of `body` as body is a parent of `li`. For example we will put a text inside and `li` element:
```javascript
newli.appendChild(document.createTextNode("This Is A Text!"));
//OR:
let ThisIsAText = document.createTextNode("This Is A Text!");
newli.appendChild(ThisIsAText);
// We can also append li inside ul element:
ulID.appendChild(newli);
```
# 6) `document.getElementsByClassName(".ok");`
## This function takes a string argument. A `.` should be present before the name of the class. It simply searches any element with the provided class and makes and Array to store what ever it finds. 
## For example if I want to remove things which someone has selected through check boxes I would do something like this:
```javascript
function removeitem (){
    let checkboxes = document.getElementsByClassName(".checkbox");
    console.log(checkboxes);
    for (let i = 0; i < checkboxes.length; i++) {
        let checkbox = checkboxes[i];
        let prei = i;  // Just check the current index again.
        if (checkbox.checked) {
            let value = checkbox.value;
            console.log("Checkbox value: " + value);
            checkbox.parentNode.parentNode.removeChild(checkbox.parentNode);
            i = prei-1; //As i will be incremented we need to decrement it.
        }
    }
}
```
## Note: Here we can see that after removing an element which was present in the Array created by the function the Array Self Arranged itself.

# 7) `document.querySelector("Anything")`;
## This function takes a string argument and simply searches for anything with that string name. It can be a class and id or an element. It just returns whatever it finds. If there are multiple things then it stores it in and array.
# 8) Storing and reading stuff in browser local storage:
## 8.1) Storing:
```javascript
localStorage.setItem("UserDataBase", JSON.stringify(UserDataBase));
// UserDataBase can be an Array or an Object or anything.
```
## 8.2) Reading:
```javascript
// Retrieve stored data from localStorage
let storedUserData = localStorage.getItem("UserDataBase");
var UserDataBase = storedUserData ? JSON.parse(storedUserData) : [];
// Now you can work with UserDataBase containing stored user data
```
-------------------------------------

# [Read More At HERE!!!!!!!!!!!!!!!!!!!!!!](https://www.w3schools.com/js/js_htmldom.asp)
# TF you doing HERE? Learn [[NPM]]!!!!!!!!!!!!!!!
