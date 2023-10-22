```javascript
const person = "Martha";

// BAD
const sayHelloBadly = function() {
  console.log(`Howdy, ${person}`);
}
sayHelloBadly(); // Works, but not ideal!

// GOOD
const sayHelloGoodly = function(name) {
  console.log(`Howdy, ${name}`);
}
sayHelloGoodly(person);
```
# Average Function
```javascript
function average(list) {
  var sum = 0;
  for( var i = 0; i < list.length; i++) {
    sum += parseInt( list[i], 10 );
  }
  return sum / list.length;
};  

console.log(average([3, 5, 7]));
```
### Using forEach Loop
```javascript
arry = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15];

function calculateAverage(array) {
    var total = 0;
    var count = 0;

    array.forEach(function(item, index) {
        total += item;
        count++;
    });

    return total / count;
}

console.log(calculateAverage(arry));
```
## Here are all 5 rules reviewed below:

1. Give your functions precise verb/action based names
2. Use camelCasedNames (like this one)
3. Properly indent the function code
4. Functions should focus on a single task: returning a value or causing a side effect. Break your function into additional smaller functions if you find it doing two or more things
    * One single task could be to compute and return a value (eg: zeroPad)
    * Another single task could be to perform a side effect such as logging a message to the screen (eg: printFarmInventory)
5. Data needed by Functions should be passed in as parameters/arguments (i.e. local scope) instead of being accessed directly


# Syntax Errors
```javascript
var rank = "Imperator";
var name = "Furiosa";

console.log(rank name);
```

```javascript
node syntax-error.js
/vagrant/focal/syntax-error.js:4
console.log(rank name);
                 ^^^^
SyntaxError: Unexpected identifier
    at exports.runInThisContext (vm.js:73:16)
    at Module._compile (module.js:443:25)
    at Object.Module._extensions..js (module.js:478:10)
    at Module.load (module.js:355:32)
    at Function.Module._load (module.js:310:12)
    at Function.Module.runMain (module.js:501:10)
    at startup (node.js:129:16)
    at node.js:814:3
```
Let's start with the first line of the error message.

```javascript
/vagrant/focal/syntax-error.js:4

```
This tells us that the error happened in a file called /vagrant/focal/syntax-error.js, but more importantly, the :4 on the end of the file name tells us the error was thrown by line 4 in this file. This is very useful, because it helps us narrow down our search for the error. Looking back at our code, we find that line 4 is the following.

```javascript
console.log(rank name);
```

```javascript
console.log(rank name);
                 ^^^^
SyntaxError: Unexpected identifier
```
This shows us where exactly in the code the error occurred and that we're dealing with a SyntaxError. There seems to be something wrong with name, which JavaScript is calling an Unexpected identifier.

Because we're working out of a single file, we can be confident we've learned enough about our error to fix it (more on why in the very next section). There's no trick for the next step; here we see that what we meant to do was log rank then name, separated by a space, which means we're missing a ,.

# Reference Errors
```javascript
var firstName = "Jane";
var lastName = "Doe";

console.log(firstName, lasName);
```

```javascript
node reference-error.js
/vagrant/focal/reference-error.js:4
console.log(firstName, lasName);
                       ^
ReferenceError: lasName is not defined
    at Object.<anonymous> (/vagrant/focal/reference-error.js:4:24)
    at Module._compile (module.js:460:26)
    at Object.Module._extensions..js (module.js:478:10)
    at Module.load (module.js:355:32)
    at Function.Module._load (module.js:310:12)
    at Function.Module.runMain (module.js:501:10)
    at startup (node.js:129:16)
    at node.js:814:3
```
This tells us our error is most likely coming from line 4, which is confirmed by the next couple lines of the error message.


```javascript
console.log(firstName, lasName);
                       ^
```
Something is wrong with lasName – node tells us that it's not defined. ReferenceErrors are also common errors we see in day-to-day development, and they occur when we're trying to use the value of an undefined variable. In our case, this happened because we misspelled lastName. Let's fix it and try the code again.
# Type Errors
```javascript
var favouriteMeal = "BREAKFAST";

console.log(favouriteMeal.toLower());
```

```javascript
node type-error.js
/vagrant/focal/type-error.js:3
console.log(favouriteMeal.toLower());
                          ^
TypeError: undefined is not a function
    at Object.<anonymous> (/vagrant/focal/type-error.js:3:27)
    at Module._compile (module.js:460:26)
    at Object.Module._extensions..js (module.js:478:10)
    at Module.load (module.js:355:32)
    at Function.Module._load (module.js:310:12)
    at Function.Module.runMain (module.js:501:10)
    at startup (node.js:129:16)
    at node.js:814:3
```
```javascript
/vagrant/focal/type-error.js:3
console.log(favouriteMeal.toLower());
                          ^
```
It's telling us we broke something on line 3, and it has something to do with toLower. It looks fine at a glance, so let's check the error description.


```javascript
TypeError: undefined is not a function
```

```javascript
var favouriteMeal = "BREAKFAST";

console.log(favouriteMeal.toLowerCase());
```