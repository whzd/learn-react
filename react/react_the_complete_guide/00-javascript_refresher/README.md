# Javascript Refresher

## Variables

Defining a variable as **var** or **let** works the same way, allows the reassign of its value.

However, defining it as **const** will give an error when trying to reassign the initial value of the variable.

## Arrow

When using a arrow function, the keyword **this** always keeps its context.

Arrow function also allow the simplification of a function that *only returns something*.
It also can be simplified further if it receives *only one argument*.

**Example without arrow**:

```js
function multiply (number) {
    return number * 2;
}
```

**Ecample with arrow**:

```js
const multiply = (number) => {
    return number *2
}
```

**Simplified example with arrow**:

```js
const multiply = number => number * 2;
```

## Exports and Imports

When a file only exports one object we use the keywords **export default**.

**Example** (person.js):

```js
const person = {
    name: 'Max'
}

export default person
```

When a file exports multiple objects, we use the keywords **export const**.

**Example** (utility.js):

```js
export const clean = () => {...}

export const baseData = 10;
```

When importing from a file that used the keyword **default** when exporting, we just need the file name, and can set the target value *as we wish*.

**Example** (app.js):

```js
import person from './person.js'
import prs from './person.js'
```

When importing from a file that didn't use the keyword **default**, it will import base on the object name, therefor *it needs to be the same*.
In this case we can set an *alias* name to the object imported.
It is also possible to import everything from a file using the *' * '* character, and still assign an *alias* to it.

**Example** (app.js):

```js
import { baseData as BD, clean } from './utility.js'
import * as utility from './utility.js'
```

## Classes

A class is created with the keyword **class** and it can have both *properties* and *methods*.

**Example**:

```js
class Human {
    this.gender = 'male';

    printGender = () => {
        console.log(this.gender);
    }
}
```

Classes also support inheritance, which allow a class to have all the *properties* and *methods* of another class and more new *properties* and *methods* of itself.

**Example**:

```js
class Person extends Human {
    this.name = 'Max';

    printMyName = () => {
        console.log(this.name);
    }
}

const person = new Person();
// Inheritance allows you to use
person.printGender();
```

## Spread and Rest Operators

The operator syntax is the same for *Spread* and *Rest* and it is **'...'** .

* *Spread* is used to add array elements or object properties to new arrays or objects.

    **Note:** On objects, using the same key that already existes on the spread values will result on its override (the new key takes precedence).

    **Example**:

    ```js
    const newArray = [...oldArray, 1, 2];
    const newObject = {...oldObject, newProp: 5};
    ```

* *Rest* is used to merge a list of function arguments into an array.

    **Example**:

    ```js
    const sortArgs = (...args) => args.sort();
    ```

## Destruction

It allows to extract array elements or object properties and store them on variables.

**Example**:

```js
const numbers = [1, 2, 3];
[num1, , num3] = numbers;
console.log(num1, num3); // 1 3

const person = {name: 'Max', age: 28};
{name} = person;
console.log(name); // Max
console.log(age); // undefined
```

# Reference and Primitive Types

Integers, strings and boolean are primitive types and when assigning a variable of one of this types to a new variable it will copy it's value.

**Example**:

```js
var num1 = 2;
const num2 = num1;
num1 = 3;
console.log(num2); // 2
```

Arrays and objects, on the other hand, are copied by reference.
This means that the pointer to their values is what is stored on the new variable.

**Example**:

```js
const person = {
    name: 'Max'
};
const secondPerson = person;
person.name = 'Manu';
console.log(secondPerson); // Manu
```

To copy the values of and object or array into another variable we can use the **spread** operator.

```js
const person = {
    name: 'Max'
};
const secondPerson = {
    ...person;
};
person.name = 'Manu';
console.log(secondPerson); // Max
```
