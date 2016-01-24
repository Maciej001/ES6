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

or you can lookup for name and assign it to firstName
```
let { name:firstName } = {
  ...,
  name: "John",
  ...
}
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