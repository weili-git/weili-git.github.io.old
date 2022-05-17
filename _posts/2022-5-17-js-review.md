---
layout: default
title: Javascript Review
description: Javascript编程语言回顾
date: 2022-5-17 9:56:00 +0800
categories: [Programming]
permalink: /:title    # permalink: /:categories/:title
---

# 1. Variable

```js
var a = 5;  // declare global
function myfunc(){
    var a = 10; // override global
    {
        let a = 5;  // local
        // here a = 5;
    }
    // here a = 10;
}
// only 'var' can override in the same block
// var a = 10;
// let a = 5;  illegal statement
```

# 2. Constant

```js
const a = 5;    // initial value must be assigned
a = 3   // illegal statement

// the atribution of constant object can be changed
const b = ["Python", "Java", "C++"];
b[0] = "Ruby";  // legal statement

// but the object itself can not be re-assigned
b = ["C#", "VB"];   // illegal statment

// more example
const car = {type:"porsche", model:"911", color:"Black"};
car.color = "White";
car.owner = "Bill";

var x = 5;
{
    const x = 10;   // here x = 10, just like 'let'
}
// here x = 5
```
# 3. Data Type
```js
//  left to right, auto type conversion
var x = 12 + 3 + "a";    // 15a
var x = "a" + 12 + 3;    // a123

var a = {name:"aaa"};
typeof a    // object

var b = undefined
typeof b    // undefined 

var c = null
typeof c    // object

b === c     // false, different type
b == c      // true, the same value

typeof funtion myfunc(){}   // function

var d = [0, 1, 2, 3];
typeof d    // array is object

```

# 4. Object

```js
var person = {
    firstName:"Bill",
    lastName:"Gates",
    age:50,
    eyeColor:"blue",
    fullName : function() {
        return this.firstName + " " + this.lastName;
        // 'this' is the owner of the function, here it's Object person
    }
};

person.firstName    // Bill
person["firstName"] // Bill
person.fullName()   // Bill Gates
```

# 5. Event

```js
<button onclick="this.innerHTML=Date()">What time is it now?</button>
```

# 6. String
```js
var x = new String("Bill");             
var y = new String("Bill"); // (x === y) is false，because x and y are different Object

var x = "Bill";             
var y = new String("Bill"); // (x == y) is true，because x and y have the same value

var str = "The full name of China is the People's Republic of China.";
var pos = str.indexOf("China");     // 17
var pos = str.lastIndexOf("China"); // 51
var pos = str.indexOf("USA")        // -1
var pos = str.indexOf("China", 18); // 51
var pos = str.lastIndexOf("China", 50); // 17
var pos = str.search("China")       // 17, only the first appearance, but support regular expression

var str = "Apple, Banana, Mango";
var res = str.slice(7,13);  //  Banana
var res = str.slice(-13,-7);    // Banana
var res = str.slice(7);     // Banana, Mang
var res = str.slice(-13);   // Banana, Mang
var res = str.substring(7, 13)  // Banana, withou negative index
var res = str.substr(7,6);  // arg2 means the length
var n = str.replace("Apple", "Orange");
var n = str.replace(/ApPle/i, "Orange");    // Case insensitive
var n = str.replace(/Apple/g, "Orange");    // replace all
var text1 = str.toUpperCase();
var text2 = str.toLowerCase();
text3 = text1.concat(" ",text2);

var str = "       Hello World!        ";
alert(str.trim());  // delete the space in the front and the end
str.charAt(0);  // H
str.charCodeAt(0);  // 72
str[0];         // H
str[0] = "A"    // does not work, no error

var txt = "a,b,c,d,e";
txt.split(",");
var txt = "Hello";
txt.split("");  // H e l l o

etc...
```

# 7. Array

```js
var arr = [1, 3, 5, 2, 4, 6];
arr.sort();
arr.reverse();
Math.max.apply(null, arr);
arr.sort(function(a, b){return a - b});
arr.forEach(myFunction);    // iteration
arr.map(myFunction);
arr.filter(lessthan0);
var sum = arr.reduce();     // the origin array doesn't change
var sum = arr.reduceRight();
var alllessthan0 = arr.every(lessthan0);
var somelessthan0 = arr.some(lessthan0);
arr.find(lessthan0);

function lessthan0(value, index, array) {
  return value < 0;
}
```

# 8. Loop

```js
const numbers = [45, 4, 9, 16, 25];

let txt = "";
for (let x in numbers) {
  txt += numbers[x];
}
numbers.forEach(myFunction);
```

# 9. JavaScript Object Notation (JSON)

```js
var text = '{ "employees" : [' +
    '{ "firstName":"Bill" , "lastName":"Gates" },' +
    '{ "firstName":"Steve" , "lastName":"Jobs" },' +
    '{ "firstName":"Alan" , "lastName":"Turing" } ]}';
var obj = JSON.parse(text);
```