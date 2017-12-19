# javaScriptEssential
javascript essential training notes

# ch6) DOM
browser is o bj
BOM - browser object model

- window.innerWidth tells you the width of your widow
- window.open() opens up new tab window

Resource
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference
list all the properties and methods for window

- window.document
one of the properties in the window object which html document sits
you can call it directly also
- document = window.document

# D OM
head vs body
- head is invisible part of document (meta, title, link)
- body has visible part

## DOM Properties
https://developer.mozilla.org/en-US/docs/Web/API/document
- document.body; // the body element
- document.title; // the document title
- document.URL; // the document URL

## DOM Methods
// Get the element with a specified ID:
document.getElementById("some-ID");

# javaScript structural outline:
- Add script tag right before closing of body tag
<!DOCTYPE HTML>
<html>
<body>
  

<script type="text/javascript">
var tabLinks;
var tabPanels;

</script>
</body>
</html>

# Ternary operator (https://watchandcode.com/courses/77710/lectures/2296260)
@ 11:21

  * formula: conditional ? (if condition is true) : conditional2 ? (else if condition2 is true) : (else default case)

  ex) accounting.js ternary operator
  ```javascript
  // Choose which format to use for this value:
    var useFormat = number > 0 ? formats.pos : number < 0 ? formats.neg : formats.zero;

  // 1st, it will check first set right before colon;
  // Is it greater than zero? then format.pos otherwise, if not: Go to next set
  column number > 0 ? formats.pos

  // is it less than zero? then format.neg, if not: Go to next set
  number < 0 ? formats.neg

  // else, it must be zero
  formats.zero
  ```

  - Better way to write this statement:

  ```javascript
  var useFormat; // not yet give it a value

  if (number > 0) {
    useFormat = formats.pos;
  } else if (number < 0) {
    useFormat = formats.neg;
  } else {
    useFormat = formats.zero;
  }
  ```

  ex) another ex from Udacity on ternary operator for if...else stmt.

  - conditional ? (if condition is true) : (if condition is false)
  ```javascript
  var isGoing = true;
  var color = isGoing ? "green" : "red";
  console.log(color);
  // output: "green"
  ```

  - rewrite to if...else
  ```javascript
  var isGoing = true;
  var color;
  if(isGoing) {
    color = "green";
  } else {
    color = "red";
  }
  console.log(color);
  ```

- Challenge advance level ternary operator:
```javascript

//ex ternary operator invoking function 
var sayHello = function () {
  console.log('Hello!');
}

var sayBye = function () {
  console.log('Bye!');
}

var friend = false;
friend ? sayHello() : sayBye();
// output bye

//ex ternary operator if..else if
var age = 20;
var personType;

if (age > 17) {
  personType = 'Adult';
} else if (age > 12) {
  personType = 'Teen';
} else {
  personType = 'Kid';
}

// ternary operator rewrite
personType = age > 17 ? 'Adult' : age > 12 ? 'Teen' : 'Kid';


// make it more readable
personType = age > 17 ? 'Adult' : 
             age > 12 ? 'Teen' : 
             'Kid';
console.log(personType); 

// one example where Ternary operation is not encouraged.
age = 20;
var isAdult;

if (age > 17) {
  isAdult = true;
} else {
  isAdult = false;
}

isAdult = age > 17 ? true : false; // only makes the code complex
isAdult = age > 17; // this is better by coersion it will assign only when true.
// Note: when you have a variable assisgnmenet t/f no need ternary nor if/else

// if there is user Action > process that action otherwise, defaultAction
var action = userAction ? userAction : defaultAction;
var action = userAction || defaultAction; // OR operation is more easy to undertand

// if..else
var action;
if (userAction) {
  action = userAction;
} else {
  action = defaultAction;
}
```
* resource: https://www.youtube.com/watch?v=0l-jPBVoARY

```javascript
/*
 * Programming Quiz - Navigating the Food Chain (3-8)
 *
 * Use a series of ternary operator to set the category to one of the following:
 *   - "herbivore" if an animal eats plants
 *   - "carnivore" if an animal eats animals
 *   - "omnivore" if an animal eats plants and animals
 *   - undefined if an animal doesn't eat plants or animals
 *
 * Notes
 *   - use the variables `eatsPlants` and `eatsAnimals` in your ternary expressions
 *   - `if` statements aren't allowed ;-)
 */

// change the values of `eatsPlants` and `eatsAnimals` to test your code
var eatsPlants = true;
var eatsAnimals = true;
var category = eatsPlants && eatsAnimals ? "omnivore" :
               eatsPlants ? "herbivore" :
               eatsAnimals ? "carnivore" :
               undefined;
```
# Switch statement

When do you use switch statement?  repeating else...if stmt in your code, where each code is based on the same value, > use switch statement.

```javascript
var option = 3;

if (option === 1) {
  console.log("You selected option 1.");
} else if (option === 2) {
  console.log("You selected option 2.");
} else if (option === 3) {
  console.log("You selected option 3.");
} else if (option === 4) {
  console.log("You selected option 4.");
} else if (option === 5) {
  console.log("You selected option 5.");
} else if (option === 6) {
  console.log("You selected option 6.");
}

// convert to switch statement
var option = 3;
switch (option) {
  case 1: 
    console.log("You selected option 1.");
    break;
  case 2: 
    console.log("You selected option 2.");
    break;
  case 3:
    console.log("You selected option 3.");
    break;
  case 4:
    console.log("You selected option 4.");
    break;
  case 5: 
    console.log("You selected option 5.");
    break;
  case 6:
    console.log("You selected option 6.");
    break; // last case 6 break is not neccessary
}
// for switch statement it is important to break; otherwise, fallthru happens
//  where after case 3 > keeps running until the end.

// quiz
var month = 2;

switch(month) {
  case 1:
  case 3:
  case 5:
  case 7:
  case 8:
  case 10:
  case 12:
    days = 31;
    break;
  case 4:
  case 6:
  case 9:
  case 11:
    days = 30;
    break;
  case 2:
    days = 28;
}

console.log("There are " + days + " days in this month.");
//28 days
```

- use case for 'falling-through' behavior for switch statement with no break
* fun card game refer:
https://www.kickstarter.com/projects/elanlee/exploding-kittens/description

```javascript
var tier = "deck of legends";
var output = "You'll receive ";

switch (tier) {
  case "deck of legends":
    output += "a custom card, ";
  case "collector's deck":
    output += "a signed version of the Exploding Kittens deck, ";
  case "nfsw deck":
    output += "one copy of the NFSW Exploding Kittens card game and ";
  default:
    output += "one copy of the Exploding Kitten card game.";
}

console.log(output);
// You'll receive a custom card, a signed version of the Exploding Kittens deck, one copy of the NFSW Exploding Kittens card game and one copy of the Exploding Kitten card game.
```

## Challenge: If winner = 3?  
```javascript
var prize = "";

switch (winner) {
  case 1:
    prize += "a trip for two to the Bahamas and ";
  case 2:
    prize += "a four piece furniture set.";
    break;
  case 3:
    prize += "a smartwatch and ";
  default:
    prize += "tickets to the circus.";
}

console.log("You've won " + prize);
// smart watch, tickets to circus
```

# Intro to Loops:
## While loops
- lab: while loops
```javascript
var x = 1;
while (x <= 10000) {
  console.log(x + " mississippi!");
  x = x + 1; //x++
}
```

  - Parts of While Loop
    1) When to start: The code that sets up the loop - defining the starting value of variable for instance.
    2) When to stop: The logical condition to test whether the loop should continue.
    3) How to get to the next item: The incrementing or decrementing step - ex) `x = x * 3`
        or `x = x - 1`

  ```javascript
  var start = 0; // 1) when to start
  while (start < 10) { // 2) when to stop
    console.log(start);
    start = start + 2; // 3) how to get to the next item
  }

/*
 * Programming Quiz: JuliaJames (4-1)
Loop through the numbers 1 to 20
If the number is divisible by 3, print "Julia"
If the number is divisible by 5, print "James"
If the number is divisible by 3 and 5, print "JuliaJames"
If the number is not divisible by 3 or 5, print the number
 */

var x = 1;

while ( x <= 20 /* your stop condition goes here */) {
    // check divisibility
    // print Julia, James, or JuliaJames
    if( x % 3 === 0 && x % 5 === 0) {
      console.log( "JuliaJames" );
    } else if ( x % 3 === 0 ) {
      console.log( "Julia" );
    } else if ( x % 5 === 0 ) {
      console.log( "James" );
    } else {
      console.log( x );
    }
    
    // increment x
    x++;
}

/*
99 bottles of juice on the wall! 
99 bottles of juice! Take one down, pass it around... 
98 bottles of juice on the wall!

98 bottles of juice on the wall! 
98 bottles of juice! Take one down, pass it around... 
97 bottles of juice on the wall!

97 bottles of juice on the wall! 
97 bottles of juice! Take one down, pass it around... 

... 
2 bottles of juice on the wall! 
2 bottles of juice! Take one down, pass it around... 
1 bottle of juice on the wall!

1 bottle of juice on the wall! 
1 bottle of juice! Take one down, pass it around... 
0 bottles of juice on the wall!

Some Notes:
    1. Note the pluralization of the word "bottle" when you go
      from 2 bottles to 1 bottle.
    2. Your text editor may try to autocorrect your ellipses ... 
      to the ellipses character … 
      Do not use the ellipses character for this quiz.    
*/

/*
 * Programming Quiz: 99 Bottles of Juice (4-2)
 *
 * Use the following `while` loop to write out the song "99 bottles of juice".
 * Log the your lyrics to the console.
 *
 * Note
 *   - Each line of the lyrics needs to be logged to the same line.
 *   - The pluralization of the word "bottle" changes from 
        "2 bottles" to "1 bottle" to "0 bottles".
 */

var num = 99;

/* your stop condition goes here */
while (num >= 1) {
    // check value of num
    // print lyrics using num
    // don't forget to check pluralization on the last line!
    // decrement num

    if ( num > 2 ) { // 99 - 3
        console.log( num + " bottles of juice on the wall! " 
            + num + " bottles of juice! Take one down, pass it around... "
            + (num - 1) + " bottles of juice on the wall!");
    } else if ( num === 2 ) { // just 2
        console.log( num + " bottles of juice on the wall! " 
            + num + " bottles of juice! Take one down, pass it around... "
            + (num - 1) + " bottle of juice on the wall!" );
    } else { // just 1
        console.log( num + " bottle of juice on the wall! "
            + num + " bottle of juice! Take one down, pass it around... "
            + (num - 1) + " bottles of juice on the wall!" );
    }

    num--;
}

// Quiz: Countdown, Liftoff! (4-3)https://classroom.udacity.com/courses/ud803/lessons/1234cec0-179b-40b6-9435-f10263c7de33/concepts/e2383410-4647-455e-92aa-f495c2753a08

`T-60 seconds
T-59 seconds
T-58 seconds
...
T-51 seconds
Orbiter transfers from ground to internal power
T-49 seconds
...
T-3 seconds
T-2 seconds
T-1 seconds
Solid rocket booster ignition and liftoff!`

var second = 60;
while (second >= 0) {
  if (second === 50){
    console.log("Orbiter transfers from ground to internal power");
  } else if (second === 31) {
    console.log("Ground launch sequencer is go for auto sequence start");
  } else if (second === 16) {
    console.log("Activate launch pad sound suppression system");
  } else if (second === 10) {
    console.log("Activate main engine hydrogen burnoff system");
  } else if (second === 6) {
    console.log("Main engine start");
  } else if (second === 0) {
    console.log("Solid rocket booster ignition and liftoff!");
  } else {
    console.log("T-" + second + " seconds");
  }
  second--;
}


var second = 60;

while (second >=0 ) {
    switch(second) {
        case 50:
            console.log("Orbiter transfers from ground to internal power");
            break;
        case 31:
            console.log("Ground launch sequencer is go for auto sequence start");
            break;
        case 16:
            console.log("Activate launch pad sound suppression system");
            break;
        case 10:
            console.log("Activate main engine hydrogen burnoff system");
            break;
        case 6:
            console.log("Main engine start");
            break;
        case 0:
            console.log("Solid rocket booster ignition and liftoff!");
            break;
        default:
            console.log("T-" + second + " seconds");
    }
    second--;
}

// take away: else if or if condtion equals case
//            else === default, remember to add break for each case, none for default
  ```

# for loop break down

for (var i = 0; i < 6; i++) {
  console.log("Print out i = " + i);
} 

https://www.youtube.com/watch?time_continue=121&v=LkRKVBzDFkE

|      i        |    i < 6      | console.log()    |
| ------------- |:-------------:| ----------------:|
| 0             |    true       |  Print out i = 0 |
| 1             |    true       |  Print out i = 1 |
| 2             | true          |  Print out i = 2 |
| 3             | true          |  Print out i = 3 |
| 4             | true          |  Print out i = 4 |
| 5             | true          |  Print out i = 5 |
| 6             | false         |                  |

# nested loops
resource: https://classroom.udacity.com/courses/ud803/lessons/1234cec0-179b-40b6-9435-f10263c7de33/concepts/3d9bed17-9034-4d36-987d-d1722b17968a

```javascript
for (var x = 0; x < 5; x++ ) {
  for (var y = 0; y < 3; y = y + 1) {
    console.log(x + "," + y);  
  }
}

Prints:
0, 0
0, 1
0, 2
1, 0
1, 1
1, 2
2, 0
2, 1
2, 2
3, 0
3, 1
3, 2
4, 0
4, 1
4, 2

debugger;
for (var x = 0; x < 3; x++) {
	for (var y = 0; y < 2; y++) {
		console.log(x + ", " + y);
	}
}

```
- Quiz 
```javascript
for (var i = 0; i <= 6; i = i + 2) {
  console.log(i);
}
```
output: 0246

- lab shortcut writing
  * summary of operators: 
    x++ or ++x // same as x = x + 1 
    x-- or --x // same as x = x - 1
    x += 3 // same as x = x + 3
    x -= 6 // same as x = x - 6
    x *= 2 // same as x = x * 2
    x /= 5 // same as x = x / 5

  * Pre-increment / Post-decrement: Adding/subtracting number before assigning to x.
Resource:
https://www.youtube.com/watch?time_continue=197&v=

```javascript
/*
 * Programming Quiz: Changing the Loop (4-4)
 */

// rewrite the while loop as a for loop
var x = 9;
while (x >= 1) {
    console.log("hello " + x);
    x = x - 1;
}

for (var x = 9; x >= 1; x--) {
  console.log("hello " + x);
}
```

* fix the error! for loop that's supposed to print the numbers 5 through 9. Fix the error! ***
```javascript
for (x < 10; x++) {
  console.log(x);
}
/*
 * Programming Quiz: Fix the Error 1 (4-5)
 */

// fix the for loop
for (var x = 5; x < 10; x++) {
    console.log(x);
}
```

** factorial - going base of recursion
https://watchandcode.com/courses/77710/lectures/2387638

```javascript
var counter = 0;

function recurse () {
	// Base case:
	if (counter === 1) {
		return 'done';
	// Recursive case:
	} else {
		counter++;
		var result = recurse();
		return result;
	}
}
```

## lab write 12! Factorial using forLoop:

```javascript
var counter = 0;

function recurse () {
	// Base case:
	if (counter === 1) {
		return 'done';
	// Recursive case:
	} else {
		counter++;
		var result = recurse();
		return result;
	}
}

/*
 * Programming Quiz: Factorials (4-7)
 Save your final answer in a variable called solution and print it to the console.
 */

// your code goes here
var solution = 12;

for ( var i = 11; i > 0; i--){
  solution *= i;
}

```
# lab nested for loop:
- Resource: https://classroom.udacity.com/courses/ud803/lessons/1234cec0-179b-40b6-9435-f10263c7de33/concepts/4999de08-ae90-41d0-bbe4-526161faee74

```javascript
/*
 * Programming Quiz: Find my Seat (4-8)
 * 
 * Write a nested for loop to print out all of the different seat combinations in the theater.
 * The first row-seat combination should be 0-0 
 * The last row-seat combination will be 25-99
 * 
 * Things to note: 
 *  - the row and seat numbers start at 0, not 1
 *  - the highest seat number is 99, not 100
 */

// Write your code here
for ( var row = 0; row <= 25; row++ ) {
  for ( var seat = 0; seat <= 99; seat++ ) {
    console.log( row + "-" + seat);
  }
}
```
# topic: function
- resource: https://www.youtube.com/watch?time_continue=100&v=VhyIn2N1T54

ex) ReverseString Function example as intro to function

```javascript
function reverseString(reverseMe) {
  var reversed = "";
  for (var i = reverseMe.length - 1; i >= 0; i--) {
    reversed += reverseMe[i];
  }
  return reversed;
}

console.log(reverseString("Julia"));
```
* Reason for `undefined`.  When a function has nothing explicitly returned > use special `return` keyword.
  ex) 
  ```javascript
  function sayHello() {
    var message = "Hello!";
    console.log(message); // since no `return` keyword it will give you undefined
  }

  // rewrite using `return` keyword
  function sayHello() {
    var message = "Hello!";
    return message; // returns value instead of printing
  }

  // function returns "Hello!" and console.log prints the return value
  console.log(sayHello());
  ```

quiz:
```javascript
function findAverage(x, y) { // x,y parameters defined during function declaration
  var answer = (x + y) / 2;
  return answer;
}

var avg = findAverage(5, 9); // 5,9 arguments passed in as function arguments
```

Are x and y parameters or arguments for this function?

x and y are parameters! They are defined in the function declaration. The values 5, and 9 are passed in as function arguments.

- summary of function lesson
What you've learned so far:
Functions package up code so you can easily use (and reuse) a block of code. Parameters are variables that are used to store the data that's passed into a function for the function to use. Arguments are the actual data that's passed into a function when it is invoked:

// x and y are parameters in this function declaration
function add(x, y) {
  // function body
  var sum = x + y;
  return sum; // return statement
}

// 1 and 2 are passed into the function as arguments
var sum = add(1, 2);
The function body is enclosed inside curly brackets:

function add(x, y) {
  // function body!
}
Return statements explicitly make your function return a value:

return sum;
You invoke or call a function to have it do something:

add(1, 2);
Returns: 3

# function lab
```javascript
function laugh() {
  return ("hahahahahahahahahaha!");
}

console.log(laugh());
```
/*
 * Programming Quiz: Laugh it Off 2 (5-2)
 *
 * Write a function called `laugh` with a parameter named `num` 
 * that represents the number of "ha"s to return.
 *
 * Note:
 *  - make sure your the final character is an exclamation mark ("!")
 Here's an example of the output and how to call the function that you will write:

console.log(laugh(3));
 */

 ```javascript

 function laugh (num) {
  var laughStr = "";
  for(var i = 1; i <= num; i++) {
    laughStr += "ha";
  }
  return laughStr + "!";
 }

 laugh (3);
```

 https://www.youtube.com/watch?time_continue=101&v=YY1QFCWGQzE
Ex) difference btwn return and console.log
  using prime number to demonstrate: Prime - the number can be only divisible of itself 
    and 1. Function isPrime() tells integer greater than 2 is prime.
 ```javascript

function isPrime(integer) {
  for (var x = 2; x < integer; x++) {
    if(integer % x === 0) {
      console.log(integer + " is divisible by " + x);
      return false;
    }
  }
  return true;
}
```
Prime number function

resource: about Scope
https://www.youtube.com/watch?time_continue=119&v=HJegRwwjYrY


- Quiz: Scope testing:

Where can you print out the value of variable c without resulting in an error?

```javascript
var a = 1;
function x() {
  var b = 2;
  function y() {
    var c = 3;
    function z() {
      var d = 4;
    }
    z();
  }
  y();
}

x();
```

The variable c is defined inside function y(), so it's accessible only inside function y(). This means it can be printed anywhere inside function y(), as well as inside any functions declared inside function y().

The inner functions y() and z() have access to their own local variables, the variables defined inside the functions they were also defined in (x() and y() functions respectively), and any global variables.

- Shadowing 
variable gets overwritten 

```javascript
var bookTitle = "Le Petit Prince";
console.log(bookTitle);

function displayBookEnglish() {
  // declare variable again prevent from overwritten
  var bookTitle = "The Little Prince"; 
  console.log(bookTitle);
}

displayBookEnglish();
console.log(bookTitle)

// Another example of shadowing
var x = 1;

function addTwo() {
  x = x + 2; 
}

addTwo(); // shadowing happens, global x is get increased by 2
x = x + 1; // 3 + 1 = 4
console.log(x); // 4 gets printed out

// example with no shadowing
var x = 1;

function addTwo() {
  var x = x + 2;
}

addTwo();
x = x + 1;
console.log(x);

```
- RECAP scope
If an identifier is declared in global scope, it's available everywhere.
If an identifier is declared in function scope, it's available in the function it was declared in (even in functions declared inside the function).
When trying to access an identifier, the JavaScript Engine will first look in the current function. If it doesn't find anything, it will continue to the next outer function to see if it can find the identifier there. It will keep doing this until it reaches the global scope.
Global identifiers are a bad idea. They can lead to bad variable names, conflicting variable names, and messy code.

Quiz on Hosting

What value will be printed to the console?

sayHi("Julia");

function sayHi(name) {
  console.log(greeting + " " + name);
  var greeting;
}

- output: undefined Julia

The function declaration is hoisted to the top of its current scope, and inside the function, the greeting variable declaration is also hoisted to the top of its function scope.
 
- Hositing: move to the top, raise by means of ropes and pulleys
  Things that gets hoisted: 
    1) function declaration are hoisted to the top of their current scope
    ex) 
```javascript
findAverage(5, 9);

function findAverage(x, y) {
  var answer = (x + y) / 2;
  return answer;
}
```
// when function is executed function declaration is hoisted upto top
- resource video: https://www.youtube.com/watch?time_continue=52&v=8z-HSS34dsM

```javascript
function sayGreeting() {
  console.log(greeting);
}

sayGreeting(); // output: Reference error since greeting is declare anywhere

// option2
function sayGreeting() {
  console.log(greeting);
  var greeting; // now declare but no assignment
}

sayGreeting(); // output: undefined since it has not assigned a value

function sayGreeting() {
  console.log(greeting);
  var greeting = "hello";
}
sayGreeting(); // output: undefined since var gets declared only value doesn't get assigned "hello" same as below.

function sayGreeting() {
  var greeting; // variable declaration is hoisted to the top
  console.log(greeting); // no assignment is made to greeting var > undefined
  greeting = "hello";
}
sayGreeting();
```
- Quiz on Hoisting:
What will print to console?

```javascript
sayHi('Julia');

function sayHi(name) {
  console.log(greeting + " " + name);
  var greeting; // greeting gets hoisted but undefined since no val is assigned.
}

// output: undefined Julia
```
- Qz 2) What value will be printed to the console?
```javascript
sayHi("Julia");

function sayHi(name) {
  console.log(greeting + " " + name);
  var greeting = "Hello";
}

// output: undefined Julia
```

* Take away: The variable declaration is hoisted to the top of current scope (the top of the function). Remember that the declaration is hoisted, not the assignment. The code inside sayHi is equivalent to:
```javascript
var greeting;
console.log(greeting + " " + name);
greeting = "Hello";
```

Qz 3)
What value will be printed to the console?
```javascript
function sayHi(name) {
  var greeting = "Hello";
  console.log(greeting + " " + name);
}

sayHi("Julia"); // Hello Julia
```
* Take away: The variable declaration and assignment are both already at the top of the function scope, so the function will print out: "Hello Julia"

- Summary about hoisting:
  * JavaScript hoists function declarations and variable declarations to the top of the current scope.
  * Variable assignments are not hoisted.
  * Declare functions and variables at the top of your scripts, so the syntax and behavior are consistent with each other.

- Lab quiz on function
/*
 * Programming Quiz: Build A Triangle (5-3)

 For this quiz, you're going to create a function called buildTriangle() that will accept an input (the triangle at its widest width) and will return the string representation of a triangle. See the example output below.

buildTriangle(10);
Returns:

* 
* * 
* * * 
* * * * 
* * * * * 
* * * * * * 
* * * * * * * 
* * * * * * * * 
* * * * * * * * * 
* * * * * * * * * *

We've given you one function makeLine() to start with. The function takes in a line length, and builds a line of asterisks and returns the line with a newline character.

function makeLine(length) {
  var line = "";
  for (var j = 1; j <= length; j++) {
    line += "* "
  }
  return line + "\n";
}
You will need to call this makeLine() function in buildTriangle().

This will be the most complicated program you've written yet, so take some time thinking through the problem before diving into the code. What tools will you need from your JavaScript tool belt? Professionals plan out their code before writing anything. Think through the steps your code will need to take and write them down in order. Then go through your list and convert each step into actual code. Good luck!
 */

// creates a line of * for a given length
function makeLine(length) {
    var line = "";
    for (var j = 1; j <= length; j++) {
        line += "* ";
    }
    return line + "\n";
}

// your code goes here.  Make sure you call makeLine() in your own code.
function buildTriangle (widthTriangleBase) {
    var triangle = "";
    for (var i = 1; i <= widthTriangleBase; i++) {
        triangle += makeLine(i); 
    }
    return triangle;
}

// test your code by uncommenting the following line
debugger;
console.log(buildTriangle(10));

- Function expression vs function declaration
[![expreeVsDeclare](https://github.com/heggy231/javaScriptEssential/tree/master/img/funcDecVsFuncExp.png "expression Vs declaration")]

