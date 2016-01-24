# ECMAScript6

## Destructuring assigment 

```
let { color, position } = { 
  color: "blue",
  name:  "John", 
  position: "Forward"
};
console.log( color );
console.log( position )
```

or you can look up for name and assign it to firstName
```
let { name:firstName } = {
  ...,
  name: "John",
  ... 
}
console.log( firstName )
```

### destucturing Arrays

```
let [first,,,,fifth] = [1, 2, 3, 4, 5];
console.log(fifth);
```

### destructuring Array of objects 

Let's grab only first name:
```
let people = [
  {
    "firstName": "Maciej",
    "lastName": "Nowakowski"
  },
  { 
    "firstName": "Gosia",
    "lastName": "Syta"
  }
];

people.forEach( ( { firstName } ) => {
  console.log( firstName );
})
```

or  take second element form the array, call it 'gosia' (an object) and then deconstruct it in the function

```
let [, gosia] = people;
function logEmail( { email } ) {
  console.log( email );
}

logEmail( gosia ); // will print "Gosia"
```

## const Declaration

Once the variable is declared as `const` it's read-only and you cannot reassign value to it.
Actually it's not constant value, but constant reference. 
const declaration has a block scope only. Outside of the block it does not exist.


## Modules

create a file `addition.js`

```
function sumTwo(a, b) {
  return a + b;
}

export { sumTwo }
```

now in your `main.js` if you want to use it:

```
import { sumTwo } from 'addition'   // <- relative path with a name of file without .js extension

```

you can `export` directly on the function definition: 
```
export function sumTwo(a, b) {...}
```

use aliases when importing 

```
import { sumTwo as addTwoNumbers }
```

import everything:

```
import * as addition from 'addition';
```

and use it like this:

```
console.log( addition.sumTwo( 1, 3 ) );
```

### Importing third-package 

1. install module `npm install --save lodash`
2. `import * as _ from 'lodash'`

use Mozilla docs or Babel docs to check how it works



## Spread Operators

instead of 

```
let first = [1, 2, 3];
let second = [4, 5, 6];

first.push( second ); 
console.log( first ); // -> [1, 2, 3, [4, 5, 6]]
```

use:


```
let first = [1, 2, 3];
let second = [4, 5, 6];

first.push( ...second ); 
console.log( first ); // -> [1, 2, 3, 4, 5, 6]
```

or you can use spread operator when passing array of arguments into the function

```
let first = [1, 2, 3];
function addThreeThings( a, b, c ) {
  console.log( a + b + c );
}

addThreeThings(...first); // -> 6
```


## Shorthand Properties - destructuring backwards

```
let fName = "Maciej";
let lName = "Nowakowski";

let user = { fName, lName };
```


## Object Enhancements

Valid syntax for declaring a function on an object:

```
let color = "red";

let car = {
  color,
  go() {
    console.log("bruuuum!");
  }
}

// or get the same using variable

let drive = "go"

let car = {
  color,
  [drive]: function() {     // or instead of variable use ["go"]:
    console.log("bruuum")
  }
}

```

## Default values for function parameters

```
function greet(greeting, name="John") {      // default parameter
  console.log(greetng + ", " + name);
}
```

passing a function: 

```
function receive(complete){
  complete();
}

receive(function() {
  console.log("complete");
});

```


## Arrow functions

In arrow functions 'this' refers still to the scope outside of the function, so you don't have to use 
`let self = this;`

```
let greeting = ( msg, name ) => msg + name;
```

or with only one parameter you can skip braces

```
let squared = x => x*x;
```


## String templates

You don't have to put new line signs
You can use expressions within the braces

```
let salutation = "Hello";

let greeting = `${salutation}, World!`

console.log(greeting);
```

You can defign the function, that will use `strings` from your string and will put them into an array
and will use `values` and put them into an array. Then it returns new transformed string.


```
function tag(strings, ...values){
  if (values[0]<20){
    values[1] = "awake"
  } else {
    values[1] = "sleepy"
  }

  return `${strings[0]${values[0]}${strings[1]}${values[1]}`
}

let message = tag`It's ${new Date().getHours()} and I'm ${""});

console.log(message);

```









































