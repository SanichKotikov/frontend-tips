# Прототип объекта

`__proto__` или `[[Prototype]]` — скрытое системное свойство, которое служит связующим звеном между объектами.

```js
var obj1 = { prop1: true };
var obj2 = { prop2: true };

obj2.__proto__ = obj1;

obj2.prop2; // obj2.prop2
obj2.prop1; // obj2.__proto__.prop1
```

Все типы данных наследуются от Object:

```js
Number.prototype.__proto__ === Object.prototype;
```

Конец цепочки:

```js
Object.prototype.__proto__ === null;
```

## Метод hasOwnProperty

Проверяет, содержит ли объект указанное свойство.

```js
var obj1 = { prop1: true };
var obj2 = { prop2: true };

obj2.__proto__ = obj1;

obj2.hasOwnProperty('prop2'); // => true
obj2.hasOwnProperty('prop1'); // => false
```

## Object.create()

Cоздаёт новый объект с указанными объектом прототипа и свойствами.

```js
const obj1 = {};
obj1.__proto__ === Object.prototype;

const obj2 = Object.create(null);
obj2.__proto__ === undefined;
```

## Ссылки

* [Object.prototype.\_\_proto\_\_](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/proto)
* [Object.prototype.hasOwnProperty()](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)
* [Object.create()](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
