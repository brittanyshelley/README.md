# package.json
Virtually all Node.js projects have a file called package.json, which looks similar to this:
```javascript
{
  "name": "project-name",
  "version": "1.0.0",
  "description": "Short project summary",
  "main": "index.js",
  "scripts": {
    "myscript": "ENV=development node index.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "MIT",
  "dependencies": {
    "express": "^4.13.4"
  }
}
```
There are some basic attributes such as the project's name, description, and author.

Custom Scripts In package.json
The scripts portion allows us to run commands using an alias, for instance:

``` javascript
npm run myscript
```
## Dependencies In package.json
The dependencies section of package.json lists the packages that need to be installed for the project to run properly. In the above example it lists a package called express, and the value ^4.13.4 specifies the version.

### Instruction
Review the full documentation of package.json from npm Docs

First, run npm init in your terminal. Just as before, feel free to just hit Enter for all the fields and use the default values to answer the questions that pop up.
```javascript
npm init
```
Now that we have our package.json file, we can install mocha and chai with one handy command:
```javascript
npm install mocha@9.2.2 chai --save-dev
```
After running this command, you should see the <font color="red">node_modules</font> folder and a <font color="red">package-lock.json</font> file appear. To make this activity a little simpler, let’s update our package.json file to use mocha for our testing.

### Instruction
Open the package.json file (note: not the lock version!). Under “scripts”, there should be a “test” key. Replace the value with “mocha”, as shown in the code snippet below.
```javascript
"scripts": {
  "test": "./node_modules/mocha/bin/mocha"
},
  ```
Save and close your package.json file. You can now run the command npm test in your terminal and npm will automatically call mocha to do its job. Go ahead and try it.

You’ll see that mocha tries to run, but it gives us an error because it has no test files to run just yet. That makes sense—we haven’t written any.

To finish our setup, inside your unit_testing folder, create two more folders: javascript and test. One is for our code, and the other is for our test files. This is a common pattern for repositories that use unit testing: one folder for the code, another to make sure it’s doing its job correctly.

> Note:
> Naming our test folder test tells mocha where to find our test files. While you could name your code folder anything you want (src is a common choice), you should keep your mocha test files in a test folder to keep things simple.

```javascript
exports.isGroupValid = function(array) {
  if (array.length >= 6) {
    return false
  } else if (array.length <= 1) {
    return false
  } else {
    return true
  }
}
```
This line allows us to define the function and export it at the same time:
```javascript
exports.isGroupValid
```
In the test folder create a file called test.js

```javascript
const chai = require('chai');  // import the chai library
const assert = chai.expect;  // establish a variable to be used in our tests
const validator = require('../javascript/groupValidator.js'); // import the file where our function lives
describe("The function groupValidator()", () => {
    // this is where we put our tests.
});
```
The <font color="pink">describe</font> line begins our testing block, and within its callback function, we’ll be writing our tests. Our tests themselves will follow a very similar pattern: a keyword, a string description, and then a callback function.

A good initial test would be to see if the function returns true for a valid group. The following code shows what that test should look like.
```javascript
it("should return true if there are between 2 and 5 group members", () => {
    assert(validator.isGroupValid(["a", "b", "c"])).to.be.true
  });
```
The it line gives a description of the test, then runs a callback function. That function finds our validator file and then runs the groupValidator function inside with the parameters we pass it. Since we’re testing a group that should work, we’ve given it an array with three strings inside.

As for assert and to.be.true, these logically declare what they’re doing. When we run the function isGroupValid() with an input of ["a", "b", "c"], we want chai to assert that the result that comes back is true.

Here's how we did it:
```javascript
it("should return false when there are fewer than 2 group members", () => {
  assert(validator.isGroupValid(["a"])).to.be.false
});
it("should return false when there are more than 5 group members", () => {
  assert(validator.isGroupValid(["a", "b", "c", "d", "e", "f"])).to.be.false
});
```
save and --save-dev : Why You Should know The Difference ...
--save-dev saves the name and version of the package being installed in the dev-dependency object. As developers who are just getting started or want to build an application that can be easily deployed without any problem this difference is a must know.