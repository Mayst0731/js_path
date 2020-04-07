## var, const, let
1. var can be overwritten in a same scope. It belongs to function scope, while let and const belong to block scope

2. var is a function 

3. let and cannot be overwritten in a same scope.In other words, the reference of the variable cannot be changed, but it's props can be changed. (Error:has already be declared)

4. Using attributes from ES5 to freeze the props from const variable to make them immutable:
```Js
    const person = {
    name: 'Jelley',
    age: 20
  }
  ```
```Js
const Jelly = Object.freeze(person);
```
## IIFE
1. As var belongs to a function scope,we could utilize this feature to avoid polluting the other variables.
   [使得变量私有化]

```JS
(function(){
 var name = 'Sarah';
})()
```
```JS
{
const name = 'Sarah';
}
```
```JS
for(var i=0;i<10;i++){
setTimeout(funtion(){
console.log(`i:${i}`);
},1000)
}
```
=>

```JS
for(let i=0;i<10;i++){
setTimeout(funtion(){
console.log(`i:${i}`);
},1000)
}
```
## Temporal Dead Zone

var => undefine
let,const => reference error

## Arrow function
```JS
const numbers = [5,6,13,0,1,18,23];

const double = numbers.map(function(number){
    return number*2 
});

const double2 = numbers.map((number)=>{
    return number * 2
});

const double3 = numbers.map(number=>number * 2
);

const double4 = numbers.map(()=>...)

const double5 = numbers.map((a,b)=>...)
```
## this
```Js
const Jelly = {
    name : 'Jelly',
    hobbies : ['Coding','Sleeping','Reading'],
    printHobbies: function(){
        this.hobbies.map(function(hobby){
            console.log(`${this.name}loves${hobby}`);
        })
    }
}
```
```Js
const Jelly = {
    name : 'Jelly',
    hobbies : ['Coding','Sleeping','Reading'],
    printHobbies: function(){
        this.hobbies.map(function(hobby){
            console.log(`${this.name}loves${hobby}`);
        })
    }
}
Jelly.printHobbies();
```JS
const Jelly = {
    name : 'Jelly',
    hobbies : ['Coding','Sleeping','Reading'],
    printHobbies: function(){
        console.log(this);
        this.hobbies.map(function(hobby){
            console.log(`${this.name}loves${hobby}`);
        })
    }
}
Jelly.printHobbies();
```
```JS
const Jelly = {
    name : 'Jelly',
    hobbies : ['Coding','Sleeping','Reading'],
    printHobbies: function(){
        this.hobbies.map(function(hobby){
            console.log(this);
            console.log(`${this.name}loves${hobby}`);
        })
    }
}
Jelly.printHobbies();
```
###### Self
```JS
const Jelly = {
    name : 'Jelly',
    hobbies : ['Coding','Sleeping','Reading'],
    printHobbies: function(){
        var self=this
        this.hobbies.map(function(hobby){
            console.log(`${self.name}loves${hobby}`);
        })
    }
}
Jelly.printHobbies();
```
###### Arrow function
```JS
const Jelly = {
    name : 'Jelly',
    hobbies : ['Coding','Sleeping','Reading'],
    printHobbies: function(){
        this.hobbies.map(hobby=>{
            console.log(`${this.name}loves${hobby}`);
        })
    }
}
Jelly.printHobbies();
```




