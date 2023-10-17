### Tips

Try experimenting with the comparison operators (`<`, `>`, `===`, etc.) in the node REPL, which you can launch using the `node` command in Vagrant.

Work on your code iteratively – that means in small pieces. 

To help you figure out how to use `hungry` and `availableTime` inside your function, try outputting their values to the Terminal as follows.
```javascript
function whatToDoForLunch(hungry, availableTime) {
  console.log("hungry is", hungry);
  console.log("availableTime is", availableTime);
}
```
```javascript
const whatToDoForLunch = function(hungry, availableTime) {
  if (!hungry) {
    console.log("Wait until your hungry");
  } else if (availableTime < 20) {
    console.log("Pick up a snack or grab something from home!");
  } else if (availableTime >= 20 && availableTime <= 30) {
    console.log("You deserve a break and should take time to cook a tasty meal!");
  } else {
    console.log("This is an intense program after all and you should probably reconsider taking a long lunch");
  }
};

console.log("I'm hungry and I have 20 minutes for lunch.");
whatToDoForLunch(true, 20);
console.log("---");

console.log("I'm hungry and I have 50 minutes for lunch.");
whatToDoForLunch(true, 50);
console.log("---");

console.log("I'm not hungry and I have 30 minutes for lunch.");
whatToDoForLunch(false, 30);
console.log("---");
```