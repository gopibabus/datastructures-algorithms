# Problem Solving

### What is an Algorithm?

A process or set of steps to accomplish certain task. Almost everything that you do in programming involves some kind of
algorithm. It's the foundation for a successful problem-solving.

### How to solve a problem?

1. Devise a plan for solving problems
    1. Understand the problem.
    2. Explore concrete examples
    3. Break it down
    4. Solve/Simplify
    5. Look back and Refactor
2. Master common problem-solving patterns

### Understand the Problem

1. Can I reinstate the problem in my own words?
2. What are inputs that go into the problem?
3. What are outputs that should come from the solution to the problem?
4. Can outputs be determined from the inputs? In other words, do I have enough information to solve the problem?
5. How should I label the important pieces of data that are part of the problem?

**Example:**<br><br>
**Question:**<br>
Write a function which takes 2 numbers and returns their sum?

**Solution:**<br>

1. Implement addition of 2 numbers
2. 2 input parameters of type int or float
3. output should be int or float
4. Yes
5. Steps
    1. Input parameter names
    2. Output variable name
    3. Intermediate variable names to store data

### Explore Concrete Examples

Coming up with examples can help to understand the problem better. Examples also provide sanity checks that our eventual
solution works how it should

1. Start with Simple Examples
2. Progress to more complex Examples
3. Explore examples with Empty Inputs
4. Explore examples with Invalid Inputs.

**Example:**<br><br>
**Question:**<br>
Write a function which takes the string and returns counts of each character in the string.

**Solution:**<br>

```js
//Step: 1
charCount("aaaa"); //{a:4}
charCount("hello"); //{e:1, h:1, l:2, o:1}

//Step: 2
charCount("my phone number is 5085302391"); //Should I inlude spaces?
charCount("Hi how are you?"); //chars in string are case sensitive or insensitive?

//Step: 3
charCount(""); //Should function return empty object or null or empty string?

//Step: 4
charCount({}); //Should function return empty object or null or empty string?
```

### Break it down

Explicitly write out steps we need to take. This forces you to think about the code you write before you write it and
helps you catch any lingering conceptual issues or misunderstandings before you dive in.

**Example:**<br><br>
**Question:**<br>
Write a function which takes the string and returns counts of each character in the string.

**Solution:**<br>

```js
function charCount(str) {
    //do something
    //return an object with lower case alpha numeric chars in string.
}

function charCount(str) {
    //Make Object to return at end.
    //Loop over the String, for each character
    //if Char is number/char and  is in Object, add one to count.
    //if Char is number/char and is not in the Object, add Char to Object with value 1
    //if Char is something else (space, period, etc.,) don't do anything.
    //Return Object at end
}
```

### Solve/Simplify

1. Find the core difficulty in what you are trying to do?
2. Temporarily ignore that difficulty
3. Write simplified solution
4. Ten incorporate difficulty back in.

**Example:**<br><br>
**Question:**<br>
Write a function which takes the string and returns counts of each character in the string.

**Solution:**<br>

```js
function charCount(str) {
    //Make Object to return at end.
    let result = {};
    //Loop over the String, for each character
    for (let i = 0; i < str.length; i++) {
        let char = str[i].toLowerCase();
        //if Char is number/char and  is in Object, add one to count.
        if (result[char] > 0) {
            result[char]++
        }
        //if Char is number/char and is not in the Object, add Char to Object with value 1
        else {
            result[char] = 1;
        }
        //if Char is something else (space, period, etc.,) don't do anything.   
    }
    //Return Object at end
    return result;
}
```

### Look Back & Refactor

* Can you check the result?
* Can you derive result differently?
* Can you understand at a glance?
* Can you use the result or method for some other problem?
* Can you improve performance of our solution?
* Can you think other ways to refactor?
* How have other people solved the problem?

```js
//Refactor : 1
function charCount(str) {
    let result = {};
    for (let i = 0; i < str.length; i++) {
        let char = str[i].toLowerCase();
        if (/[a-z0-9]/.test(char)) {
            if (result[char] > 0) {
                result[char]++
            } else {
                result[char] = 1;
            }
        }
    }
    return result;
}

//Refactor : 2
function charCount(str) {
    let result = {};
    for (let char of str) {
        char = char.toLowerCase();
        if (/[a-z0-9]/.test(char)) {
            result[char] = ++result[char] || 1;
        }
    }
    return result;
}

//Refactor : 3
function isAlphaNumeric(char) {
    var code = char.charCodeAt(0);
    if (!(code > 47 && code < 58) && // numeric (0-9)
        !(code > 64 && code < 91) && // upper alpha (A-Z)
        !(code > 96 && code < 123)) { // lower alpha (a-z)
        return false;
    }
    return true;
}

function charCount(str) {
    let result = {};
    for (let char of str) {
        if (isAlphaNumeric(char)) {
            char = char.toLowerCase();
            result[char] = ++result[char] || 1;
        }
    }
    return result;
}
```
