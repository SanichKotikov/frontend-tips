# "Поднятие" (Hoisting)

Все переменные _поднимаются_ в начало функции:

```js
var scope = "global";

function f() {
    console.log(scope);  // Выведет "undefined", а не "global"
    var scope = "local"; // Инициализируется здесь, а определена везде
    console.log(scope);  // Выведет "local"
}
```

Этот код, в действительности, будет выполнен следующим образом:

```js
var scope = "global";

function f() {
    var scope;
    console.log(scope);
    scope = "local";
    console.log(scope);
}
```

## let и const

`let` и `const` тоже всплывают, но их поведение отличается:

```js
let x = 'outer scope';

(function() {
    console.log(x); // => ReferenceError
    let x = 'inner scope';
}());
```

Cвязано это с [Temporal Dead Zone](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified/).
