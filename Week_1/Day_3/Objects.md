# Objects
In JavaScript, when you use square brackets to access an object's property, the key should be a string. If it's not a string, JavaScript treats it as a variable. So in this case, firstName is treated as a variable, and since it's not defined, you get a ReferenceError.

Here's how you could use a variable to access an object's property:
```javascript
const person = { firstName: "Khurram" };
const propertyName = "firstName";
const firstName = person[propertyName};]
```
### Assigning a new value to a key
```javascript
const mary = { name: "Mary Sue" };
mary["name"] = "Mary Jane";
mary["age"]  = 22;
mary 
//Returns
{ name: 'Mary Jane', age: 22 }
```
We reviewed the most common way to create objects (const o = {}), accessing and setting properties on objects using string keys (o["key"]) as well as how to get a list of all the keys in an object (Object.keys(o)).

## Creating Object
```javascript
var planetMoons = {
  mercury: 0,
  venus: 0,
  earth: 1,
  mars: 2,
  jupiter: 67,
  saturn: 62,
  uranus: 27,
  neptune: 14
};
```
In the above example, our planetMoons object has 8 keys - one for each planet in our solar system.

We can traverse all the properties of this object using a for-loop, like so:
```javascript
for (var planet in planetMoons) {
  var numberOfMoons = planetMoons[planet];
  console.log("Planet: " + planet + ", # of Moons: "+ numberOfMoons);
}
```
We have the key available to us within the scope of the loop; in the above example it is the planet variable. Notice how we access the object using a variable, planetMoons[planet]. The variable planet iterates over each key ("mercury", "venus", ...) using the for-loop.

objects can sometimes have properties that they inherit from their prototype chain as well as method names. An additional filtering step is sometimes necessary:

```javascript
for (var planet in planetMoons) {
  // additional filter for object properties:
  if (planetMoons.hasOwnProperty(planet)) {
    //  ...
  }
}
```