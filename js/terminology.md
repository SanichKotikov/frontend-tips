# Терминология

* [Чистые функции (Pure Functions)](#чистые-функции-pure-functions)
* [Функции высшего порядка (Higher Order Functions)](#функции-высшего-порядка-higher-order-functions)

***

## Чистые функции (Pure Functions)

Функция является чистой, если:

* все данные, с которыми она работает, передаются как аргументы;
* она ни чего не изменяет (переданные или любые инные данные);
* с одинаковыми аргументами она всегда возвращает одинаковый (предсказуемый) результат.

Пример:

```js
function sum(x, y) {
    return x + y;
}
```

## Функции высшего порядка (Higher Order Functions)

Это функция, которая возвращает другую функцию. Пример:

```js
function logAndReturn(func) {
    return function() {
        var args = Array.prototype.slice.call(arguments);
        var result = func.apply(null, args);
        console.log('Result', result);
        return result;
    }
}
```
