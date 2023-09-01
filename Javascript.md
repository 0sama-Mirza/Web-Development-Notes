# 1) How to run it?
-----------------
#### - Through a browser.

#### - Through NodeJS (V8 engine inside C++).
###### -----> AKA javascript runtime. 
-----------------
# 2) Variables 
-----------------
### 2.1) var : Global, Can be re-declared.
### 2.2) let : Local, Normal Variable. 
### 2.3) const : Constant
e.g:
```javascript
var a = "Global";
let b = "Local";
{
	let b = 1;
	consol.log("b = ",b,"\na = ",a);
}
consol.log("b = ",b,"\na = ",a);
```
```output
Output:
b = 1
a = Global
b = Local
a = Global
```
-----------------
# 3) Primitives Data Types and Objects:
-----------------
## 3.1) Primitive = Built in data types:
### - 7 Primitive data types:
+ N- NULL
+ N- Number
+ S- Symbol
+ S- String
+ B- Boolean
+ B- BigInt
+ U- Undefined
```javascript
let a = null;
let b = 69;
let c = Symbol("I am a nice symbol");
let d = "I am a string";
let e = true;
let f = BigInt("69420");
let g = undefined;
```
### 3.2) Non-Primitive Data Type:
#### - Objects/Dictionary:
```javascript
const Student {
	name: "Name",
	gpa: 2.8,
	pass: false,
	number: 03175477177,
}
Student.name;
```
#### - Arrays:
```javascript
const array_name = [item1, item2, ...];
```
#### 3.2.1) Reference Type:
##### - In Non-Primitive Data Type when we do `obj2 = obj1` they will be the same thing. `obj2` will be a reference to the `obj1`. Its like a pointer. e.g:
```javascript
a = [1,2,3,4];
b = [1,2,3,4];
a === b;
// false
a = b;
a === b;
// true
``` 
-----------------
# 4) JAVASCRIPT FUNCTIONS
-----------------
```javascript
// Function Expresion:
var a = function name(a=1,b=2) {
	return a+b;
}
// // Function Declaration:
function add(a=1,b=2) {
	return a+b;
}
// ECMAScript 6:
const add2 = (a=1,b=2) => a+b; // If there are no {} then it automatically returns whatever the expression is.
add2() // Output: 3
const add3 = (a=1,b=2) => {a+b};
add3() // Output: Undefined
```
## Function Expressions vs. Function Declarations:

| Aspect                  | Function Expressions               | Function Declarations            |
|-------------------------|------------------------------------|----------------------------------|
| Definition Syntax       | Assigned to a variable or property | Defined using the `function` keyword |
| Hoisting                | Not hoisted (Is not moved to the top by the compiler)| Hoisted to the top of scope (Is Moved At The Top By The Compiler)     |
| Anonymous Functions     | Can be anonymous (unnamed)         | Named functions                 |
| Use as Arguments        | Can be passed as arguments         | Can be passed as arguments      |
| Use as Callbacks        | Often used for callbacks           | Can be used for callbacks       |
| Use in IIFE (Immediately Invoked Function Expressions) | Commonly used in IIFE           | Not commonly used in IIFE       |
| Flexibility             | Provides more flexibility          | Limited flexibility in placement |
| Usage in Scope          | Must be defined before use        | Can be called before definition |
| Examples                | `const add = function(a, b) {...};` | `function subtract(a, b) {...}` |
| Best for               | More specific use cases, closures  | General-purpose, reusable functions |
### 4.1) Function Declaration:
```javascript
// Calling the function before its definition because the compiler automatically moved it at the top.
result = add(3, 5); // This works!
function add(a, b) {
    return a + b;
}
console.log(result); // Output: 8
```
### 4.2) Function Expression:
```javascript
result = a(3, 5);
VM14:1 Uncaught ReferenceError: a is not defined
let a = function(a,b){
	return a + b;
}
```
#### 4.2.1)  Named Function Expression:
##### The name of the function is only accessible inside the function scope. 
```javascript
const factorial = function calcFactorial(n) {
    if (n <= 1) {
        return 1;
    }
    return n * calcFactorial(n - 1); // Using the named function inside itself
};
const greet = function sayHello(name) {
    console.log(`Hello, ${name}!`);
};
greet("Alice"); // Outputs: Hello, Alice!
sayHello("Bob"); // ReferenceError: sayHello is not defined
```
#### 4.3) Arrow Functions:
##### Note: arrow functions are not part of `window`. We cannot do `window.arrowfunction()`.
##### 4.3.1) Currying (A function within a function):
```javascript
const multiply = (a, b) => a*b;
const curriedmultiply = (a) => (b) => a*b;
curriedmultiply(3); // Output: (b) => a*b; (It returned a function)
curriedmultiply(3)(5); // Output: 15
const times69 = curriedmultiply(69); // 1st function's argument which is a=69
times69(6); //Output: 414
```
##### 4.3.2) Compose (Put 2 or more functions together to form a 3rd function where the output of 2nd/1st function is the input of the other):
```javascript
const compose = (f,g) => (a) => (b) => f(g(a))+b;
                  ^       ^      ^        ^
//Functions #:   1st     2nd    3rd      4th         
// f and g are functions:
const sum = (num) => num + 69;
compose(sum,sum)(6)(1);
// 1. The sum of g(6) will be executed which is 6+69 = 75 so `g(a) = 75`
// 2. The sum of f(75) will be executed which is 75+69 = 144 so `g(a) = 144`
// 3. 144 + 1 = 145
```
 -----------------
 # 5) CONST:
 ## + const for primitive data types works just like C++. We cannot change the value and its data type.
 ```javascript
 const a = 1;
 a = 2;
 VM162:1 Uncaught TypeError: Assignment to constant variable.
```
## + const for non primitive data types:
###  - Const Objects's items can be edited and new items can be added. Const only makes it impossible to make the object variable change its data type:
```javascript
const obj = {
    Name : "Osama",
}
obj // Output: {Name: 'Osama'}
obj.Location = "Pakistan";
obj // Output: {Name: 'Osama', Location: 'Pakistan'}
obj = 69;
Uncaught TypeError: Assignment to constant variable.
```
### - Const Array are similar:
```javascript
const cars = ["Saab", "Volvo", "BMW"];
cars.push("Mehran");
cars // Output: ['Saab', 'Volvo', 'BMW', 'Mehran']
cars[0] = 69;
cars // Output: [69, 'Volvo', 'BMW', 'Mehran']
cars = 69;
Uncaught TypeError: Assignment to constant variable.
```
 ---------------
 # 6) Copy data from objects (Modern way):
 ```javascript
 const obj = {
	 player: "Osama",
	 xp: 40,
	 wizardlevel: 69,
 }
 // Old Way:
 const player = obj.player;
 const xp = obj.xp;
 const wizardlevel = obj.wizardlevel;
 // New Way:
 const { player, xp } = obj;
 const { wizardlevel } = obj;
```
## Note: When using `{} = obj` make sure to use the same name as the name of the items inside the object. Meaning you cannot do `{ok,pk} = obj;`.
## 6.1) Reference Type:
### Objects are reference types. They donot copy data as they dont have a copy constructor/function. So when you do `=` their address/reference is assigned to each other. Its like pointers. It doesnt happen in primitive datatype as we how we will copy the things.
```javascript
[] === [] // False
[1] === [1] // Flase
const obj = {value: 10};
const obj2 = {value: 10};
obj === obj2 // False
obj1 = obj
obj1 === obj // True
obj1.value = 15;
console.log(obj.value) // 15
```
 ### 6.2) Shallow Copy:
 #### In order to copy we use: `object = { ...object1}`. Here are some examples:
 ```javascript
 let Name = {
    name: "Osama"
};
NameAge = Name;
NameAge.age = 69;
consol.log(Name); // Output: {name: 'Osama', age: 69}
// Name and NameAge are now intermingled 
NameAgeLocation = {...obj};
NameAgeLocation.country = "Pakistan";
console.log(Name); //Output: {name: 'Osama', age: 69} 
console.log(NameAgeLocation); //Output: {name: 'Osama', age: 69, country: 'Pakistan'}
```
### 6.3) Deep Copy:
#### Shallow Copy can only copy the first level inside the object. Meaning if an object has another object inside it that object will be passed by reference. In order to copy the second level we need deep copy. Here are some examples:
```javascript
let obj = {
	a: "a",b: "b",c: {deep: "Try To Copy Me :)"}
};
let ShallowCopy = {...obj};
let DeepCopy = JSON.parse(JSON.stringify(obj));
obj.c.deep = "Nigga";
console.log("obj: ",obj);
console.log("Shallow Copy: ",ShallowCopy);
console.log("Deep Copy: ",DeepCopy);
```
```output
obj:  {a: 'a', b: 'b', c: {deep: 'Nigga'}}
Shallow Copy:  {a: 'a', b: 'b', c: {deep: 'Nigga'}}
Deep Copy:  {a: 'a', b: 'b', c: {deep: 'Try To Copy Me :)'}}
```
 ---------------
 # 7) Modern way to make an object:
 ## - Insert same value and key inside object:
 ```javascript
 const a = 1;
 const b = "two";
 const c = {};
 const obj = {a,b,c};
```
## - Make Keys Dynamic:
```javascript
const Name = "User Name";
const obj = {
	[UserName] : "Osama",
	[1+3] : 69,
}
```
  ---------------
  # 8) Arrays/List/Object:
  ## [A Great Resource](https://sdras.github.io/array-explorer/)
---------------
  ## 8.1) How to loop in Array:
  1. `for.Each`
  2. `for (let i=0l i< array.length; i++)`
  3. `while()`
  4. `for of` Only for Array/List
  5. `for in` 
  ```javascript
const array = [1,2,3,4];
const newarray = [];
array.forEach((num) => { // num will store one of the array's item value.
    newarray.push(num * 2);
});
// 1) forEach function takes a function as a perimeter/argument.
// 2) The passed function should contain a num argument where it will store the //    actual value of each item's value of the array.
// 3) forEach will just loop and do whatever the function says.
// Same as:
const array = [1,2,3,4];
const newarray = [];
const double = (num) => { // num will store one of the array's item value.
    newarray.push(num * 2);
} 
array.forEach(double);
// Old Version:
for (let i = 0; i < array.length; i++){
	newarray.push(2 * array[i]);
}
```
```output
Output: newarray = [2,4,5,8]
```
### 8.1.1) `for of's` syntax is as follows:
#### - `for` (`random_variable_name` of `name_of_the_array`){}
```javascript
const basket = ["Apple","Banana","Coconut","Grapes","Mango","Orange"];
for (fruit of basket){
	console.log(fruit);
}
```
### 8.1.2) `for in's` syntax is as follows:
#### - `for` (`random_variable_name` in `name_of_the_object`){}
#### - `random_variable_name` = keys.
```javascript
const basket = {
	"Apples": 10,
	"Banana": 40,
	"Cononut": 100,
}
for (fruits in basket){
	console.log(fruits);
}
```
## See 14.3) Expanded Object's Methods just like Python.
## 8.2) Array Methods:
1. map
2. filter
3. reduce
## 8.3) map:
`map` will loop over the array just like `forEach` but `map` will store the values generated inside the loop in a new array so we can return it. Just like `forEach` it takes a function as an argument.:
```javascript
const array = [1,2,3,4];
const newarray = array.map((num) => num * 2);
// Alternative:
const array = [1,2,3,4];
const double = (num) => num * 2;
const newarray = array.map(double);
```
```output
Output: newarray = [2,4,5,8]
```
## 8.4) filter:
`filter` will use `>` `<` `===` or boolean answers to filter out the array and store it in another array just like map:
```javascript
const array = [1,2,3,4];
const filterarray = array.filter((num) => num > 3);
// Or
const array = [1,2,3,4];
const greaterthan2 = (num) => num > 2;
const filterarray = array.filter(greaterthan2);
```
```output
Output: filterarray = [3,4]
```
### Note: `num` will the actual value of the `array[index]` meaning first time filterarray's num will have value = `1` even though we are at `array[0]`.  
## 8.5) reduce:
`reduce` takes 2 parameters/arguments. 1st is a function with 2 arguments. 2nd is the value of the 1st function's 1st argument which is the accumulator:
```javascript
const array = [1,2,3,4];
const reducedarray = array.reduce((accumulator,num) => accumulator + num, 0);
// OR:
const array = [1,2,3,4];
const KeepOnAdding = (acc,num) => acc + num;
const reducedarray = array.reduce(KeepOnAdding,0);
```
```output
Output: 10
```
## NOTE:
## ALL OF THESE ARRAY METHODS NEED `num` AS AN ARGUMENT. MAYBE BECAUSE WE ARE GIVING IT A DATATYPE INSTEAD OF A VARIABLE NAME.
-----------------
# 9) This:
-----------------
## `this` refers to the object environment that we are in right now. E.G:
```javascript
function fun () {
	console.log(this)
}
fun(); // Output: window
// This Changed:
const obj1 = {
    "fun" : function () {
        return console.log(this);
    }
}
obj1.fun(); // Output: {fun: ƒ}
```
## Lets Look At Each Case:
1. **Global Context:**
   In the global context, `this` refers to the global object. In a browser environment, the global object is usually `window`.

   ```javascript
   console.log(this); // Outputs: Window
   ```

2. **Function Context:**
   Inside a regular function, the value of `this` depends on how the function is called:

   - If the function is called as a method of an object, `this` refers to that object.
   - If the function is called without any context, `this` will default to the global object.

   ```javascript
function greet() {
    console.log(this);
}
const person = {
    name: "Alice",
    sayHello: greet
};
person.sayHello(); // Output: {name: 'Alice', sayHello: ƒ}
greet(); // Output: Window {window: Window, self: Window, document: document, name: '', location: Location, …}
   ```
1. **Arrow Functions:**
   Arrow functions have a different behavior with `this`. They capture the value of `this` from their enclosing context, which makes them useful for avoiding issues with nested functions.

   ```javascript
   const person = {
       name: "Bob",
       sayHello: function() {
           setTimeout(() => {
               console.log(`Hello, ${this.name}`);
           }, 1000);
       }
   };

   person.sayHello(); // Outputs: Hello, Bob
   ```

4. **Explicit Binding:**
   You can explicitly set the value of `this` using methods like `call`, `apply`, and `bind`.

   ```javascript
   function greet() {
       console.log(`Hello, ${this.name}`);
   }

   const person1 = { name: "Alice" };
   const person2 = { name: "Bob" };

   greet.call(person1); // Outputs: Hello, Alice
   greet.apply(person2); // Outputs: Hello, Bob

   const greetAlice = greet.bind(person1);
   greetAlice(); // Outputs: Hello, Alice
   ```

5. **Constructor Functions:**
   Inside a constructor function, `this` refers to the instance being created. Constructor functions are used to create objects based on a blueprint.

   ```javascript
   function Person(name) {
       this.name = name;
   }

   const alice = new Person("Alice");
   console.log(alice.name); // Outputs: Alice
   ```

6. **DOM Event Handlers:**
   When a function is used as an event handler for a DOM element, `this` usually refers to the element that triggered the event.

   ```javascript
   const button = document.querySelector("button");

   button.addEventListener("click", function() {
       console.log(this); // Outputs: <button> element that was clicked
   });
   ```
-----------------
# 10) Class:
-----------------
## Unlike C++ where we declare variables inside the class here we don't declare variables inside the class. Instead we need a constructor function. But that is a function so any variables declared inside it would be local. So we use `this` to make them the variables of the class rather than the function.
### Example #1(Javascript):
```javascript
class Player {
    constructor(name, age, country) {
        this.name = name;
        this.age = age;
        this.country = country;
        console.log(this);
    }
}
class Wizard extends Player {
	constructor(name, age, country, NickName) {
		super(name, age, country); // super = constructor of Player
		this.NickName = NickName;
	}
}
```
### C++ Equivalent:
```cpp
class Player {
	private:
		string name;int age;string country;
	public:
		Player(const string& name,const int& age,const string& country) : name(name), age(age), country(country) {}
}
class Wizard : public Player {
	private:
		string NickName;
	public:
		Wizard(const string& name,const int& age,const string& country, const string& NickName) : name(name), age(age), country(country), NickName(NickName) {}
}
```
### Example #2:
#### Javascript:
```javascript
class Animal {
	constructor(name,color,sound){
		this.name = name;
		this.color = color;
		this.sound = sound;
	}
	introduce = () => {
		console.log(`${this.sound}!\nMy Name Is ${this.name}\nI Am A ${this.type}\nMy Color Is ${this.color}`);
	}

class Mammal extends Animal{
	constructor(name,color,type,sound){
		super (name,color,sound);
		this.type = type;
	}
}
const Cow = new Mammal("Billo","White and Black","Cow","Moooo");
const cat = new Mammal("Tom", "gray", "cat", "Meow");
Cow.introduce();
cat.introduce();
```
#### C++:
```cpp
#include<iostream>
#include<string>
class Animal {
	private:
		std::string name,color,sound;
	public:
		Animal(const std::string& name,const std::string& color,const std::string& sound): name(name), color(color), sound(sound) {}
		void introduce () {
			std::cout<<this->sound<<"!\nMy Name Is "<<this->name<<"\nMy Color Is "<<this->color;
		} 
};
class Mammal: public Animal {
	private:
		std::string type;
	public:
		Mammal(const std::string& name,const std::string& color,const std::string& sound, const std::string& type): Animal(name, color, sound), type(type) {}
		void introduce(){
			Animal::introduce();
			std::cout<<"\nI Am A "<<this->type;
		}
};
int main(){
	Mammal Cow("Billo","White and Black","Moooo","Cow");
	Mammal cat("Tom", "gray", "Meow", "Cat");
	Cow.introduce();
	std::cout<<std::endl;
	cat.introduce();
	std::cout<<std::endl;
	return 0;
}
```
-----------------
 # 11) Type Coercion:
 ## It means changing one datatype into another. Read about it at:
1. [The Abstract Equality Comparison Algorithm](https://www.ecma-international.org/ecma-262/5.1/#sec-11.9.3)
2. [Equality comparisons and sameness](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness)
3. [JavaScript Equality Table](https://dorey.github.io/JavaScript-Equality-Table/)

-----------------
# 12) EC7 (ES2016):
## 12.1) .include():
### Checks in a string or array if something is in it or not. Returns `true` or `false`. E.G:
```javascript
"Osama".includes("O"); // Output: true
const pets = ["Cat","Dog","Parrot",69];
pets.include("Bird") // Output: false
pets.include(69) // Output: true
```
## 12.2) Exponential/Power:
### `**` = Power:
```javascript
const square (x) => x**2; 
```
-----------------
# 13) ES8 (ES2017):
## 13.1) Padding In Strings:
### `.padStart()` and `.padEnd()` takes 1 argument of type `num`. It makes the total string into that length inside the argument by adding spaces at the end or start. If the argument's length is more then the string's length then it will add more spaces until the total length of the string matches the argument. Else it will do nothing. Example:
```javascript
"Osama".padStart(10); // Output: "     Osama"
"Osama".padEnd(5); // Output: "Osama"
```
1. As "Osama".length() === 5 it added 5 spaces at the start. Now the total.length() = 10.
2. As "Osama".length() === 5 there will be no change. If it was`padEnd(1)`still it would do nothing.
## 13.2) `,` at the end of function parameters/arguments is now valid:
```javascript
fun (a,b,c,d,) => concole.log(a);
fun(1,2,3,4,); // Output: 1
```
## 13.3) Expanded Object's Methods just like Python:
1. `Object.keys(obj)` Grabs the keys of the object.
2. `Object.values(obj)` Grabs the value of the object.
3. `Object.entries(obj)` Grabs the key and value and stores them in an Array/List.
Examples:
```javascript
const obj = {
	name: "Osama",
	age: 22,
	country: "Pakistan",
}
```
1. ```javascript
Object.keys(obj).forEach((key,value) => {
	console.log(key,": ",obj[key]);})
// Output:
name: Osama
age: 22
country: Pakistan
2. ```javascript
Object.values(obj).forEach(value => {
	   console.log("Value: ",value)})
// Output:
Osama
22
Pakistan
3. ```javascript
Object.entries(obj).forEach(value => {
	console.log(value);})
// Output:
[name: "Osama"]
[age: 22]
[country: "Pakistan"]
# 13.4) Async Await:

-----------------
# 14) ES10 (ES2019):
## 14.1) `.flat()` takes num argument telling at of how many layers/times should it flaten. Default is 1:
```javascript
array = [1,[2,3],4,[5,6],7];
array.flat(); // Output: [1,2,3,4,5,6,7]
array2 = [1,[2,3],4,[5,[6],7]];
array2.flat(); // Output: [1,2,3,4,5,[6],7]
array2.flat(2); // Output: [1,2,3,4,5,6,7]
array3 = [1,2,,,,,,,4,5,6];
array3.flat(); // Output: [1,2,4,5,6]
```
## 14.2) `.flatmap()` takes a function as an argument. It first flattens the Array and then performs `.map()` function:
```javascript
array4 = ["Cat",["Dog","Mouse"],"Lion","Tiger",[69,["Nice","Elephant"]]];
const array4withParrots = array4.flatMap (creatures => creatures + " Parrots");
```
```javascript
console.log(array4withParrots);
// Output:
['Cat Parrots', 'Dog,Mouse Parrots', 'Lion Parrots', 'Tiger Parrots', '69,Nice,Elephant Parrots']
// Note: The num 69 became a string.
```
# 14.3) `.trim()`removes white spaces:
```javascript
"     This string has whitespaces         ".trim()
// Output:
This string has whitespaces
```
# 14.4) `fromEntries()` simply uses ES8's `entries()` written in 14.3 of this document and instead of making arrays from objects it makes object from arrays:
```javascript
const userProfile = [["Osama",69],["Bilal",96],["Burhan",100]];
Object.fromEntries(userProfile);
// Output:
{Osama: 69, Bilal: 96, Burhan: 100}
```
# 14.5) `try{catch{}}` like C++.

-----------------
# 15) ES11 (ES2020):
## 15.1) BigInt:
### Write a number and add n at the end.
### [Read More At Here!](https://stackoverflow.com/questions/307179/what-is-javascripts-highest-integer-value-that-a-number-can-go-to-without-losin)
## 15.2) Optional Chaining Operator?:
### `object-name?.object-key?.object-key-property`
### Checks if some key exists in an object and if it does it does the job as if there are no `?` :
```javascript
const Osama = {
	ps2: {
		model: "slim",
		year: 2010,
	}
}
const Obama = {
	ps3: {
		model: "big",
		year: 2013,
	}
}
let ObamaModel = Obama?.ps2?.model;
let OsamaModel = Osama?.ps2?.model;
console.log("Obama's PS2 Model: ",ObamaModle);
console.log("Osama's PS2 Model: ",OsamaModle);
```
```output
Obama's PS2 Model:  undefined
Osama's PS2 Model:  slim
```
## 15.3) Nullish Coalescing Operator ??:
### In 15.2 the `?.` worked for the object's key but not what was at the end of it. We could use:
### `let ObamaModel = Obama?.ps2?.model || "no model";`. This means if `?.` is unable to find model then `ObamaModel = no model`. What if `model = 0`. It has something but because javascript has Type Coercion the 0 is changed into undefined. We dont want no model in ObamaModel we want 0. In order to solve that we use:
```javascript
const Obama = {
	ps3: {
		model: 0,
		year: 2013,
	}
}
let ObamaModel = Obama?.ps3?.model?? "no model"; // Output: 0 
let ObamaModel = Obama?.ps3?.model || "no model"; // Output: no model
```
---------------
 # 16)  JAVASCRIPT KEYWORDS:
-----------------
1. break
2. case
3. catch
4. class
5. const
6. continue
7. debugger
8. default
9. delete
10. do
11. else
12. export
13. extends
14. finally
15. for
16. function
17. if
18. import
19. in
20. instanceof
21. new
22. return
23. super
24. switch
25. this
26. throw
27. try
28. typeof
29. var
30. void
31. while
32. with
33. yield
-----------------
 # 16) Now Learn Some Web API like The [[DOM]].

