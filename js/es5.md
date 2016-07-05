# Изменения ECMAScript 5

[Таблица поддержки стандарта](support.md#ecmascript-5)

## Новые возможности

* Strict Mode: `'use strict';`
* Геттеры и Сеттеры: `var obj = { get foo() { return 'abc' } };`

## Синтаксис

* Возможно использовать зарезервированные слова в объектах: `var obj = { new: 'abc' };`
* Валидная запятая в конце объектов и массивов: `[3,]` и `{ prop: 3, }`
* Multiline string literals `?`

## Новые функции в стандартных объектах

### Object

* `Object.keys()`
* `Object.getOwnPropertyNames()`
* `Object.create()`
* `Object.getPrototypeOf()`
* `Object.getOwnPropertyDescriptor()`
* `Object.defineProperty()`
* `Object.defineProperties()`
* `Object.preventExtensions()`
* `Object.isExtensible()`
* `Object.seal()`
* `Object.isSealed()`
* `Object.freeze()`
* `Object.isFrozen()`

### Function

* `Function.prototype.bind()`

### String

* `String.prototype.trim()`
* Доступ к символам с помощью скобок `[...]`

### Array

* `Array.isArray()`
* `Array.prototype.map()`
* `Array.prototype.filter()`
* `Array.prototype.forEach()`
* `Array.prototype.reduce()`
* `Array.prototype.every()`
* `Array.prototype.indexOf()`
* `Array.prototype.lastIndexOf()`
* `Array.prototype.some()`

### Date

* `Date.now()`
* `Date.prototype.toISOString()`

### JSON

* `JSON.parse(text, reviver?)`
* `JSON.stringify(value, replacer?, space?)`
* `Boolean.prototype.toJSON()`
* `Number.prototype.toJSON()`
* `String.prototype.toJSON()`
* `Date.prototype.toJSON()`
