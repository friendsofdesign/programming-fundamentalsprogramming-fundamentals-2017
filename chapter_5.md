# Syntax 101

## Simple Variable

Below is the most simple syntax to declare a variable in code. We will touch on
more advanced methods to declare variables in the next course. Variables are
core to the syntax without them it would be very hard to write successful code,
this syntax will become habit in time.

```javascript
var myNewVariable = 42;
```

The variable is started with the shorthand `var` followed by the chosen
identifier and set with an assignment operator of `=` to the value of `42`

## Variable with an Expression

```javascript
var myExpression = 42 + 6;
```

This variable has a simple operand expression, it simply adding two values with
the use of an arithmetic operator.

## Variable with Operand Expression of Two Variables

```javascript
var priceOne = 42;
var priceTwo = 6;
var totalPrice = priceOne + priceTwo;
```

The first and second variables are provided with literal (static) values, the
third variable “totalPrice” uses an expression to add the two variables together
to create the total.

## Functions

You will be using functions in almost all the coding you do. You will become
very familiar with this syntax in time.

```javascript
function mySpecialFunction(parameterOne, parameterTwo) {
  // here we will place our code statements
}
```

> **NB!**
>
> Remember all parameters defined in a function like “parameterOne” are
> variables in the scope of the function. See variable scope.

## Calling Functions

For a function to be run it must either be called in code or run as method on an
event or action. To call the function I’ve declared previously I would simply
call it when I need it to run. This may be in a condition or just at the end of
the code.

```javascript
mySpecialFunction();
```

To call a function simply give the name of the function ­remember to check
spelling ­with parentheses at the end and semi­colon to close the statement.
Functions can also call other previously defined functions, this is referred to
as "Nested Functions".

```javascript
function myGlobalFunction (scope) {
  scope = "this variable is in the scope of the global function";
  console.log(scope);

  function changeVariableData () {
    scope = "this function can change the value of the variable";
    console.log(scope);
  }

  changeVariableData();
}

myGlobalFunction();
```

In the function above we can see that we have nest the the function
`changeVariableData` inside the function `myGlobalFunction`. You will also
notice the that our parent variable (`myGlobalFunction`) calls the nested
function before it is closed and outside the `myGlobalFunction` function, the
parent function is called.

When this set of nested functions is called, it will change the value of our
argument (variable) `scope` to a string value and then log it to the console
window. Then the function will call the nested function `changeVariableData`,
which will in turn change the value of our original variable `scope` to a new
string value and then proceed to log it to the console window.

Notice that the variable `scope` has only been declared once as an argument of
the function. This variable has a local scope to the parent function, however
because the second function is nested and is a child of the first function
(`myGlobalFunction`) the variable has a global scope with regards to the child
function. Any functions nested in the parent will have global access to the
variable `scope`.

## Conditional Statements

As mentioned previously, there are a number of conditional statements used in
programming. We will be looking at the most commonly used `if` statement to
provide us with an idea of the basic syntax that is similar to all conditional
statements.

```javascript
if(mySpecialVariable == 4) {
  console.log(mySpecialStatement);
}
```

Conditional statements check to see if specific arguments are met. In the
example above our condition is simply to check to see if the variable
­`mySpecialVariable` ­is strictly equal to a value of `4`, if the argument passed
into the if statement is met, we the log the variable value to the console
window.

```javascript
if(myOtherVariable != 4) {
  console.log("It’s not equal to 4!")
}
```

In the second example above we are created an argument that is using a logic
operator. The logic operator `!=` is used to check if our variable
`myOtherVariable` is "not equal to" a value of `4`. Should the `myOtherVariable`
not resolve to a value of 4, it will log to the console window a string that
reads "It’s not equal to 4!"".

> **NB!**
>
> Remember arguments are the variables and values in an expression passed into
> the parentheses of a function or conditional statement.


## Pulling It All Together in Simple System

Now you have some idea of what’s going on ­ if you don’t, don’t worry you will
get there. We are now going to pull all these previous ideas and structures into
a logic process using all the basic elements of the code.

Let's determine our logic first. We will need to ask a number of questions
before we begin to get an idea of what the this little system must do as well as
the process and order it will do it in.

1. Create a User Story ­How would we describe this process in basic spoken
   language? (e.g. english) I'm becoming very forgetful, and I would like a tool
   that will let me know if today is my birthday at the click of a button.
2. Define the Functionality ­ What does our simple system need to do?
   It needs to do a check to see if today is my birthday and let me know, when I
   click on a button.
3. Breakdown the Functions into Parts ­ What are the different parts of the
   process? We need to know what today’s date is. We need to know when my
   birthday is. We need a button that will execute the function to compare
   today’s date with my birthday to check if today is my birthday. Thereafter we
   need to show what the results are.
4. Check for User Input ­ When the user engages with the system should something
   happen? When the user clicks the "check my birthday" button, we check to see
   if today is the user’s birthday.
5. Test! Test! Test! ­ What will be final outcome of the logic process?
   That we have either confirmed or denied that today is the user’s birthday.

You can see that point 1 and 2 are basically the same, however in larger more
complex systems, asking similar questions from different perspectives can reveal
small details that may be overlooked. It is good practise to ask many questions
and to soundboard your thoughts with your team or your
friend/girlfriend/yourself if working alone.

Now that we know what we must build and how it must work, we can begin writing
the logic (code) of the application. Let's look at the logic, we need to know
today's date &  my birth date , let's define the basic variables.

```javascript
var todaysDate;
var birthdayDate;
```

Now let's assign some static values to the date variables. We will deal with
dynamic variables and dynamic data in the next course.

```javascript
var todaysDate = "August 25";
var birthdayDate = "January 15";
```

Again let's look to the logic to see what will be next. Or logic tells us we
need a button to call the function. We will now create some HTML for the basic
UI elements the user will engage with. We are going to make a simple button
object and a paragraph, each with an id and class as needed.

```html
<button id="button">Check my Birthday</button>

<p id="results" class="results"></p>
```

As you can see the paragraph is empty. It will be the wrapper/container object
that receives the message text to inform the user of what has occurred. If we
again look at the logic we can see we will need a place to display the message,
but also need to send a specific message based on whether it's my birthday or
not. For this we will define two variables one for each message type.

```javascript
var messageBirthday = "Hey look at that, it's my birthday!";
var messageNotBirthday = "Aww, it's not your birthday, sorry...";
```

We now have the dates, messages and the basic HTML in place. Now we need to make
the code react to the user and do a check to see if the dates correspond. In
this case according to our dates we can anticipate that the dates will not
match, thus we will be testing with `false` in mind. That is to say, we expect a
result that is not my birthday.

```javascript
function checkDates() {
  // conditional statement
  if (todaysDate == birthdayDate) {
    // our code will go here
  }
}
```

We have the basic `if` statement in place to being the check, but once again we
must look to the logic to see what must happen based on which condition is met
true or false. According to our logic the user must receive a message let's them
know whether it's my birthday or not. So we will need to show our messages we
created previously to the user.

To do this we need to interact with the HTML objects we created. We need to use
JavaScript to identify them and then based on what happens interact with them,
by passing data to them or calling an function or both. But how do we do this?
It works as such.

```javascript
document.getElementById('elementId');
```

The line code above will ask our document (webpage) to identify the object with
an id of "results". Once we have identified it we can work with it. So let's
identify our basic HTML objects and store them in variables for later.

```javascript
var showResults = document.getElementById('results');
var checkMyBirthday = document.getElementById('button');
```

Now we need need to put the correct message in our results container based on
the condition. We will need to adjust our `if` statement to become an `if else`
statement to switch between the messages.

```javascript
function checkDates() {
  // conditional statement
  if (todaysDate == birthdayDate) {
    // first action here
  } else {
    // second action here
  }
}
```

We have adjusted our `if` statement, declared all the variables we need, now we
need to complete our function.

```javascript
function checkDates() {
  // Conditional statement
  if (todaysDate == birthdayDate) {
    // If the dates are the same put messageBirthday into our resultscontainer.
    showResults.innerHTML = messageBirthday;
  } else {
    // If the dates are not the same put messageNotBirthday into our results container.
    showResults.innerHTML = messageBirthday;
  }
}
```

> **NB!**
>
> `.innerHTML = x;` is a javscript method which allows us to change html content
> inside an html tag.

We have completed the `checkDates` function it will run and compare the values
of the variables we defined as our dates to see if they correspond and then send
the message which is most appropriate to the results container. However our
logic says that this must happen on a button click. We have already defined our
button in a variable. We need only link the functions to the button.

```javascript
checkMyBirthday.addEventListener('click', function () {
  checkDates();
}, false);
```

So we have created a click function using an `addEventListener`, the event
listener will wait till a specific event occurs before it is run. In this case
it waits for the click. Then inside the click function we execute our
`checkDates` function we already created.

The whole code should look like this:

```html
<script type="text/javascript">
  var todaysDate = "August 25";
  var myBirthday = "August 25";

  var showResults = document.getElementById('results');
  var checkMyBirthday = document.getElementById("button");
  var messageBirthday = "Hey look at that, it's my birthday!";
  var messageNotBirthday = "Aww, it's not your birthday, sorry...";

  function checkDates() {
    if (todaysDate == myBirthday) {
      showResults.innerHTML = messageBirthday;
    } else {
      showResults.innerHTML = messageNotBirthday;
    }
  }

  checkMyBirthday.addEventListener('click', function () {
    checkDates();
  }, false);
</script>
```

And the HTML like this:

```html
<button id="button">Check My Birthday</button>
<p id="results" class="results"></p>
```

There you have it, using many of the basic elements of JavaScript you have
created a little system using logic, to determine whether two values match. Your
function also interacts directly with HTML objects and stores values in them.
These are the fundamentals of programming.

A system's complexity may increase and methods they use may be more complex,
however the fundamentals remain the same. In time you will come to know
JavaScript better and it will become far easier to write good code. Well done.
