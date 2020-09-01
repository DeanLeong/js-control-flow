
# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)  SOFTWARE ENGINEERING IMMERSIVE

# Control Flow & Loops

### Objectives
*After this lesson, students will be able to:*
- Implement `if/else` and `switch` statements and contrast use-cases
- Implement `while`-loops and understand how to break
- Identify the 4 components of a `for`-loop and their execution order
- Compare the use-cases of `for` and `while`-loops

# Conditional Statements

## if...else statement

`if` statements are an extremely common way to manage application logic —— what happens when, etc.

```js
if (/* whatever's in here is true */) {
  // this code runs
}
```

... means run the `code` block if `expr` is truthy

```javascript
if (true) {
  console.log('Hello')
}

if (1 > 0) {
  console.log('World')
}
//=> Hello
//=> World
```

When you need to test more than one case, you may use `else if`:

![flowchart](if-else-flowchart.jpg)

```javascript
const favoritePet = 'cat';

if (favoritePet === 'dog') {
  console.log('Achoo!!! Im allergic to dogs.');
} else if (favoritePet === 'cat') {
  console.log('Yeah!! Cats are the best.');
} else {
  console.log(`Please don't tell me you own a ferret`);
}

//=> Yeah!! Cats are the best.
```

When you're comparing variables to values, make sure you're using  `===` —— not `=`. If you use `=`, you're reassigning the variable, instead of checking it for equality.

### 🚀 Independent Practice!!

Touch a new javascript file —— `control-flow.js` —— and work in that. 

Let's see if you have enough money to buy a cat! Using the following terms, create an `if / else if / else` conditional statement:

- If `yourMoney` is equal to `catPrice`, log the message "You have just enough to buy a cat!"
- If `yourMoney` is more than `catPrice`, log the message "You can buy a cat and will have <X> dollars left over"
- If `yourMoney` is less than `catPrice`, log the message "You cannot buy a cat.  You need <X> more dollars :("

Check your code with the following variables (Remember, you can use Node to run the file in your terminal: `node control-flow.js`)

1) 
```js
const yourMoney = 50
const catPrice = 100
```

2) 
```js
const yourMoney = 100
const catPrice = 100
```

3) 
```js
const yourMoney = 200
const catPrice = 100
```

If you get stuck, talk to your neighbor and see if you can work it out.


### Ternary Operator

`(condition) ? ifTrue : ifFalse`

JavaScript has a ternary operator for quick conditional expressions. Where an `if ... else` **statement** conditionaly runs code, a ternary is used to make an **expression** which returns a value conditionally. Consider the difference when distinguishing between a statement and an expression:

```javascript
const age = 12

let allowed

if (age > 18) {
  allowed = 'yes'
} else {
  allowed = 'no'
}

console.log(allowed)
```

```javascript
const age = 12

const allowed = (age > 18) ? 'yes' : 'no'

console.log(allowed)
//=> "no"
```

## Switch Statement

The switch statement can be used for multiple branches based on `===` equality:

```javascript
const food = 'apple';

switch(food) {
  case 'pear':
    console.log('I like pears');
    break;
  case 'apple':
    console.log('I like apples');
    break;
  case 'orange':
    console.log('mmm... citrus');
    break;
  default:
    console.log('idk what that is');
}
//=> I like apples
```

In this case the `switch` statement compares `food` to each of the cases (`pear` and `apple`), and evaluates the expressions beneath them if there is a match. (Using `===` to evaluate equality)

The default clause is technically optional but in most cases it is good practice to include one.

### 🚀 Independent Practice!!

Now complete the following exercise in your `control-flow.js` file.

Using the example above as a guide, construct a `switch` statement to inform us if some number `n` is prime.
- If it's 1, log the message '1 is actually not prime!'
- If it's 2, log the message '2 is the smallest prime!'
- If it's 3, 5, or 7, log the message: '`n` is prime!' (use string interpolation to show the value of `n` instead of the letter "n")
- If it's 4, 6, 8, or 9, log the message: '`n` is not prime :('
- Otherwise, log the message "idk if `n` is prime. google it, ask yourself, ask your friend."

Test your code in the terminal by running `node switch-practice.js`. Try it several times giving `n` different values to make sure each part of your switch statement is functioning properly. Be careful to match the proper syntax!


# Iteration

### [`while`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/statements/while) loops

`while` is a loop statement that will run while a condition evaluates to truthy.
**WARNING** if your `while` loop never evaluates to falsy you may be stuck in an infinite loop!

```javascript
let n = 0
while (n < 50) {
  console.log(`${n} is ${n % 2 ? 'odd' : 'even'}`)
  n++
}
```
A simpler version of the code broken down.

```javascript
let n = 0
while(n < 50) {
  if (n % 2) {
    console.log(`${n} is odd`)
  } else {
    console.log(`${n} is even`)
  }
  n++
}
```

>note: remember that `n++` is the equivolent of `n = n + 1`, so basically it makes `n`'s value increase by 1 each time you loop through the code.

You can also `break` to exit the loop before the condition is met.

```javascript
let n = 0
while (n < 50) {
  console.log(`${n} is ${n % 2 ? 'odd' : 'even'}`)
  if (n === 42) {
    break
  }
  n++
}
```

### [`for`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/statements/for) loops

`for` loops contain 4 components:
- _initialization_ (e.g. `let i = 0;`)
- _test condition_ (e.g. `i < 10;`)
- _final expression_ or _incrementor_ (e.g. `i++`)
- _block_ (e.g. `console.log(i)`)

Notice these components all exist in our `while` example above. A `for` loop is just a specialized while loop since the pattern is so common.

```javascript
// start at i = 0; continue while i < 10; add 1 to i after each iteration
for (let i = 0; i < 10; i++) {
  console.log(i);
  // do more stuff
}
```
What will we see when running the above snippet?
What is the final value of `i`?

```javascript
let i = 0;
while(i < 10) {
  console.log(i);
  // do more stuff

  i++;
}
```

We can implement something similar to a `for` loop with a `while` loop.

### Looping through Arrays
One of the most common ways that we'll use loops in real life is by looping through arrays.

```javascript
const food = ['tacos', 'burritos', 'pizza', 'soup', 'pasta']
```
Now we iterate over the food array.

```javascript
for(let i = 0; i < food.length; i++) {
  console.log(food[i])
}
```

Now for something a bit more challenging, looping through an array of objects. For example, let's say that we have the following array of wizards:
```
const wizards = [
  {name: "Harry Potter", house: "Gryffindor"}, 
  {name: "Lord Voldomort", house: "Slytherin"}, 
  {name: "Cedric Diggory", house: "Hufflepuff"},
  {name: "Luna Lovegood", house: "Ravenclaw"},  
  {name: "Albus Dumbledor", house: "Gryffindor"}, 
  {name: "Merlin", house: "Slytherin"}, 
  {name: "Pomona Sprout", house: "Hufflepuff"}, 
  {name: "Gilderoy Lockheart", house: "Ravenclaw"}, 
  {name: "Ron Weasley", house: "Gryffindor"}, 
  {name: "Severus Snape", house: "Slytherin"}, 
  {name: "Nymphadora Tonks", house: "Hufflepuff"}, 
  {name: "Padma Patil", house: "Ravenclaw"}, 
  {name: "Hermoine Granger", house: "Gryffindor"} 
 ]
 ```
 
If we wanted to print the name of each wizard, we could use a `for loop` to iterate through this array. To do so, we use `i` to correspond to the `index` number of each object in the array:
```
for(let i = 0; i < wizards.length; i++){
    console.log(wizards[i].name)
}
```

#### How could we combine an `if` statement with a `for loop` to print only the names of Slytherins?

## Conclusion
- When would use conditionals? What are the different ways to tackle conditional logic?
- What can we use `for` and `while` loops to accomplish?
- How do we choose between using a `for` or a `while` loop?
