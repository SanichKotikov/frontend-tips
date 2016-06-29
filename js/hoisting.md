# "Поднятие" (Hoisting)

Все переменный "поднимаются" в начало функции:

```js
var scope = "global";

function f() {
    console.log(scope);  // Выведет "undefined", а не "global"
    var scope = "local"; // Инициализируется здесь, а определена везде
    console.log(scope);  // Выведет "local"
}
```

Этот код, в реальности, будет выполнен следующим образом:

```js
var scope = "global";

function f() {
    var scope;
    console.log(scope);
    scope = "local";
    console.log(scope);
}
```
