# JavaScript Cheat Sheet (Part - 02)

---

## JavaScript Array

```javascript
var num = [1, 2, 3, 4];

num.at(1)                           // 2
num.push(5)                         // Add element to the end: [1, 2, 3, 4, 5]
num.pop()                           // remove last element: [1, 2, 3]
num.fill(1)                         // fill every element: [1, 1, 1, 1]
num.shift()                         // remove first element: [2, 3, 4]
num.unshift(5)                      // Add element to beginning: [5, 1, 2, 3, 4]
num.reverse()                       // sort in descending order: [4, 3, 2, 1]
num.includes(2)                     // is array contains a specified value: true
num.map( item => 2*item)            // Map elementsz; [2, 4, 6, 8]
num.filter( item => item > 2)       // filter elemet: [3, 4]
num.find(item => item > 2)          // Find element : 3(first match)
num.every(item => item > 0)         // true
num.findIndex(item => item === 2)   // 1
num.reduce( (prev, curr) => prev + curr, 0) // 10
num.toString();                     // convert to string
num.join(" * ");                    // join: "1 * 2 * 3 * 4"
num.splice(2, 0, "i", "p");         // add elements : [1, 2, 'i', 'p', 3, 4]
num.slice(1,4);                     // slice elements from [1] to [4-1]
num.sort();                         // sort string alphabetically

x.sort(function(a, b){return a - b}); // numeric sort
x.sort(function(a, b){return b - a}); // numeric descending sort
x.sort(function(a, b){return 0.5 - Math.random()}); // random sort
```

---

## JavaScript Dates

```javascript
var d = new Date();

Date("2017-06-23");                      // date declaration
Date("2017");                            // is set to Jan 01
Date("2017-06-23T12:00:00-09:45");       // YYYY-MM-DDTHH:MM:SSZ
Date("June 23 2017");                    // long date format
Date("Jun 23 2017 07:45:00 GMT+0530");   // time zone

a = d.getDay();                          // getting the weekday

getDate();                               // day as a number (1-31)
getDay();                                // weekday as a number (0-6)
getFullYear();                           // four digit year (yyyy)
getHours();                              // hour (0-23)
getMilliseconds();                       // milliseconds (0-999)
getMinutes();                            // minutes (0-59)
getMonth();                              // month (0-11)
getSeconds();                            // seconds (0-59)
getTime();                               // milliseconds since 1970
```

---

## Error Handling

```javascript
try { // block of code to try
    undefinedFunction();
}
catch(err) { // block to handle errors
    console.log(err.message);
}
```

### Input Validation
```javascript
var x = document.getElementById("mynum").value;

try {
    if(x == "") throw "empty";          // error cases
    if(isNaN(x)) throw "not a number";
    x = Number(x);
    if(x > 10) throw "too high";
}
catch(err) {                            // if there's an error
    document.write("Input is " + err);  // output error
    console.error(err);                 // write the error in console
}
finally { // executed regardless of the try / catch result
    document.write("</br >Done");
}
```

---

## JavaScript JSON

```javascript
var str = '{"names":[' +                // create JSON object
    '{"first":"Hakuna","lastN":"Matata" },' +
    '{"first":"Jane","lastN":"Doe" },' +
    '{"first":"Air","last":"Jordan" }]}';

myObj = JSON.parse(str);                // parse
document.write(myObj.names[1].first);   // access
var myJSON = JSON.stringify(myObj);     // stringify
localStorage.setItem("testJSON", myJSON); // storing data
text = localStorage.getItem("testJSON"); // retrieving data
```

---

## JavaScript Object

```javascript
var student = {                         // object name
    firstName:"Jane",                   // list of properties and values
    lastName:"Doe",
    age:18,
    height:170,
    fullName : function() {             // object function
        return this.firstName + " " + this.lastName;
    }
};

student.age = 19;                       // setting value
student[age]++;                         // incrementing
name = student.fullName();               // call object function
```

---

## JavaScript Events

| Category | Events |
| :--- | :--- |
| **Mouse** | `onclick`, `oncontextmenu`, `ondblclick`, `onmousedown`, `onmouseenter`, `onmouseleave`, `onmousemove`, `onmouseover`, `onmouseout`, `onmouseup` |
| **Keyboard** | `onkeydown`, `onkeypress`, `onkeyup` |
| **Frame** | `onabort`, `onbeforeunload`, `onerror`, `onhashchange`, `onload`, `onpageshow`, `onpagehide`, `onresize`, `onscroll`, `onunload` |
| **Form** | `onblur`, `onchange`, `onfocus`, `onfocusin`, `onfocusout`, `oninput`, `oninvalid`, `onreset`, `onsearch`, `onselect`, `onsubmit` |
| **Drag** | `ondrag`, `ondragend`, `ondragenter`, `ondragleave`, `ondragover`, `ondragstart`, `ondrop` |
| **Animation** | `animationend`, `animationiteration`, `animationstart` |
| **Media** | `onabort`, `oncanplay`, `oncanplaythrough`, `ondurationchange`, `onended`, `onerror`, `onloadeddata`, `onloadedmetadata`, `onloadstart`, `onpause`, `onplay`, `onplaying`, `onprogress`, `onratechange`, `onseeked`, `onseeking`, `onstalled`, `onsuspend`, `ontimeupdate`, `onvolumechange`, `onwaiting` |
| **Miscellaneous** | `transitionend`, `onmessage`, `onmousewheel`, `ononline`, `onoffline`, `onpopstate`, `onshow`, `onstorage`, `ontoggle`, `onwheel`, `ontouchcancel`, `ontouchend`, `ontouchmove`, `ontouchstart` |
