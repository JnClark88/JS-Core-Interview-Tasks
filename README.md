# JS-Core-Interview-Tasks
practical Tasks for JS core interview
- [Variables, Values, Types](#variables-values-types)
- [Expressions, Operators, Statements](#expressions-operators-statements)
- [Arrays](#arrays)
- [Functions](#functions)
- [Advanced Functions](#advanced-functions-this-)
- [Closures](#closures)



### Variables values types

```javascript
let a = 5;

function test() {
    a = 10;
    
    return a;
    
    function a(){};
}
```
Temporary dead zone(easy)
```javascript
console.log(a);
let a = 5;
```

```javascript
let a = 5;

function test() {
   console.log(a);
   
  let a = 10;
}
```

```javascript
({} == {})

true == 'true'

'155' == 155
```

```javascript
let a = 5;

if (true) {
    console.log(a);
    let a = 10;
}
```

```javascript
function a(){}

var a = 10;

console.log(a)
```

```javascript
let id1 = Symbol("id");
let id2 = Symbol("id");

console.log(id1 == id2);
```

### Expressions, Operators, Statements (literals, conditions, loops), destructuring, string templating

```javascript
const user = {
    name: 'Test User',
    id: 0,
    role: 'default'
};

const { name, role } = user;

console.log(name, role);
```

```javascript
const user = {
    name: 'Test User',
    id: 0,
    role: 'default'
};

function parseUserToString() {
    //...your code goes here
}

parseUserToString(user) // Current user is: Test User with default role
```

### Arrays (create, indexes, length, modification, built-in methods: sorting, filtering, search, iterating, static methods)

```javascript
const array = new Array(3);
const array2 = new Array(3,3,3);

// -> add new element to the end of the array 
```

```javascript
const array = new Array(3);

array.length = 1;

console.log(array);
```

```javascript
const array = ['b', 'c', 'a', 'd', 'e'];

array.sort();

console.log(array);
```

```javascript
const array = [1,2,3,4,5,6,7,8,9];

// -> filter for odd
// -> multiply for 3
// -> return sum of all elements
```

```javascript
const array = [
    {
        id: 0,
        name: 'User0'
    },
    {
        id: 1,
        name: 'User1'
    },
    {
        id: 2,
        name: 'User2'
    },
    {
        id: 3,
        name: 'User3'
    },
    {
        id: 4,
        name: 'User4'
    }
];

// find and return user with id: 3
```

### Functions (create, invoke, arrow functions, rest operator, default parameters)

```javascript
function infiniteArguments(...rest) {
    console.log(rest);
};

infiniteArguments(1,2,3,4,5,6,7,8);
```

```javascript
function getUser({ name, id}) {
    console.log(name, id);
};

getUser({});
getUser();
```

```javascript
const x = () => console.log(arguments)

console.log(x())
```


### Advanced Functions (arguments, 'this' scope, call, apply methods, recursion)

##### Advanced Functions (*this* )

```javascript
class Rabbit {
    constructor(name) {
        this.name = name
    }

    printRabbitName() {
        return this.name
    }

    static printName() {
        return this.name
    }
}
  
const bunny = new Rabbit('Rodger')

bunny.printRabbitName()
Rabbit.printName()
```

```javascript
let greetings = {
    name:"Epam",
    sayHi(){
        return "Hello" + this.name
    }
}

const helloEpam = greetings.sayHi;
helloEpam()
```

```javascript
function sum() {
    //...you code goes here
}

sum(1) // 1
sum(1,2) // 3
sum(1,2,3) // 6
sum(1,2,3,4) // 10
```

##### Closures

```javascript
let a = 5;

function test() {
    console.log(a);
}

(function() {
    let a = 10;
    test()
})();
```
```javascript
function aprover(numberOfAproves) {
    //...your code goes here
}

const requestApprove = aprover(3)

requestApprove() // approved
requestApprove() // approved
requestApprove() // approved
requestApprove() // denied
```

##### Prototypal Inheritance

```javascript
function Rabbit(name) {
    this.name = name
}

const rabbit = new Rabbit('Rodger')

rabbit.__proto__ // ?
rabbit.prototype // ?
```
```javascript
class Rabbit {
    constructor(name) {
        this.name = name
    }
    
    jump() {
        return 'hop!'
    }
}

const bugsBunny = new Rabbit('Bugs')

bugsBunny.hasOwnProperty(bugsBunny.jump)
```

### Basic Async JavaScript (Timers, Promise)

```javascript
Promise.resolve(4)
    .then(()=>{
        console.log('first then')
    })
    .then(x=>{
        console.log('second then=', x)
    })


setTimeout(()=>{
    console.log('timeout');
})
```

###JavaScript built-in collections (Set, Map, WeakSet, WeakMap)

- new Map() – создаёт коллекцию.
- map.set(key, value) – записывает по ключу key значение value.
- map.get(key) – возвращает значение по ключу или undefined, если ключ key отсутствует.
- map.has(key) – возвращает true, если ключ key присутствует в коллекции, иначе false.
- map.delete(key) – удаляет элемент по ключу key.
- map.clear() – очищает коллекцию от всех элементов.
- map.size – возвращает текущее количество элементов.

В отличие от обычных объектов Object, в Map перебор происходит в том же порядке, в каком происходило добавление элементов.

Первое его отличие от Map в том, что ключи в WeakMap должны быть объектами, а не примитивными значениями:

```javascript
let weakMap = new WeakMap();

weakMap.set("test", "Whoops");
```

```javascript
let john = { name: "John" };

let weakMap = new WeakMap();
weakMap.set(john, "...");

john = null;
```
