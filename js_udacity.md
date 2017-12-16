





# Function
### Parameters vs. Arguments
At first, it can be a bit tricky to know when something is either a parameter or an argument. The key difference is in where they show up in the code. A parameter is always going to be a variable name and appears in the function declaration. On the other hand, an argument is always going to be a value (i.e. any of the JavaScript data types - a number, a string, a boolean, etc.) and will always appear in the code when the function is called or invoked.

In short, the parameter is: function(x,y)
the argument is: function(1,2)



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
