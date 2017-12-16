

# Points
```
// init variable and += 
var res = null; // cannot work, 
var res;   // undefined
// should be 
var res = "";

```


# Object
- typeof  
returns the name of the data type that follows it.
var umbrella = {
  color: "pink",
  isOpen: false,
  open: function() {
    if (umbrella.isOpen === true) {       // why here is not this? 
      retuen "The umbrella is already opened!";
        } else {
            umbrella.isOpen = true;
            return "Julia opens the umbrella!";
        }
    },
}
# array
### common
```
pop()       // remove the last one
reverse()
shift()     // remove the first and return it.
unshift()   // adds one or more elements to the beginning of an array and returns the new length of the array.
splice()    // replace or insert
slice()     // copy from start to end.
concat()    // merge two or more arrays.
join()      // joins all elemnets of an array into a string and returns this string.  join('-')
sort()      // sort all key/value pairs in place and return undefined.
organize()  // 
fill()      // fills all the elements of an array from a start index to an end index with a static value.
copyWithin()// 

```
### forEach
```
function myfun(element, index, array){}
arr.forEach(myfun)

// eg:
words.forEach(function(word, num, all){
  console.log("Word " + num + " in " + all.toString() + " is " + word);
});
// and don't need to 3 parameters, just this order.

```
### map
1. 1 argument
2. return a new array
### splice
While push() and pop() limit you to adding and removing elements from the end of an array, splice() lets you specify the index location to add new elements, as well as the number of elements you'd like to delete (if any).
```
var donuts = ["glazed", "chocolate frosted", "Boston creme", "glazed cruller"];
donuts.splice(1, 1, "chocolate cruller", "creme de leche"); // removes "chocolate frosted" at index 1 and adds "chocolate cruller" and "creme de leche" starting at index 1
```
Returns: "chocolate frosted"
donuts array: ["glazed", "chocolate cruller", "creme de leche", "Boston creme", "glazed cruller"]
### toUpperCase


# Function
### Parameters vs. Arguments
At first, it can be a bit tricky to know when something is either a parameter or an argument. The key difference is in where they show up in the code. A parameter is always going to be a variable name and appears in the function declaration. On the other hand, an argument is always going to be a value (i.e. any of the JavaScript data types - a number, a string, a boolean, etc.) and will always appear in the code when the function is called or invoked.

In short, the parameter is: function(x,y)
the argument is: function(1,2)
### shadowing
The variable will be changed because of function, and this variable is not the parameter.
OR,
the variable isn't announced.
```
var x = 1;

function addTwo() {
  x = x + 2;
}

addTwo();
x = x + 1;
console.log(x);

var x = 1;

function addTwo() {
  var x = x + 2;
}

addTwo();
x = x + 1;
console.log(x);
```


# Conditionals
### Truthy values
```
true
42
"pizza"
"0"
"null"
"undefined"
{}
[]
```


# Data type
### null, undefined, NaN
- null  
null is value of nothing, has value, but value is null.
- undefined  
undefined is doesn't have a value yet.
- NaN
NaN stands for "Not-A-Number" and it's often returned indicating an error with number operations. 
For instance, if you wrote some code that performed a math calculation, and the calculation failed 
to produce a valid number, NaN might be returned.
```
// calculating the square root of a negative number will return NaN
Math.sqrt(-10)

// trying to divide a string by 5 will return NaN
"hello"/5
```

### 
##### Implicit type coercion
JavaScript is known as a loosely typed language.
when your code is interpreted by the JavaScript engine it will automatically be converted into 
the "appropriate" data type.
```
"1" == 1
// true
"julia" + 1
// "julia1"
```
##### Strict equality
=== 
```
"1" === 1
// false
```




```
document.body.addEventListener('click', function () {
     var myParent = document.getElementById("Banner"); 
     var myImage = document.createElement("img");
     myImage.src = 'https://thecatapi.com/api/images/get?format=src&type=gif';
     myParent.appendChild(myImage);
     myImage.style.marginLeft = "160px";
});
```
