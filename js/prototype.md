# Object.prototype

Само по себе, без вызова оператора new, оно вообще ничего не делает, его единственное назначение — указывать `__proto__` для новых объектов.

Функции в JavaScript имеют свойство `prototype`. Оно по умолчанию является объектом с единственным свойством `constructor`, которое ссылается на саму функцию.

```js
const fn = function(){};
fn.prototype.something = 'something';

const obj = new fn();
obj.something; // => obj.__proto__.something
```

## Ссылки

* [Object.prototype](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype);
