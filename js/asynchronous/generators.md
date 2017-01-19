# Генераторы

Генератор — специальный итерируемый объект возвращаемый _функцией-генератором_ `function*`:

```js
// функция-генератор GeneratorFunction(),
function* gen() { 
    yield 1;
    yield 2;
}

// которая возвращает объект Generator { }
const g = gen();
```

Вызов `g.next()` запускает выполнение функции до ближайшего `yield` и возвращает объект `{ value, done }`,
где `value` — значение возвращаемое `yield`, а `done` — статус генератора:

```js
g.next(); // => Object {value: 1, done: false}
g.next(); // => Object {value: 2, done: false}
g.next(); // => Object {value: undefined, done: true}
```

### yield

Оператор `yield` работает в обе стороны, т.е. он может не только возвращать значение из функции-генератора,
но и передовать извне внутрь:

```js
function* gen() {
    // yield возвращает 2,
    // а затем записывает 6 в val, переданное через следующий вызов next
    const val = yield 2;
    return val * 2;
}

const g = gen();

g.next();  // => Object {value: 2, done: false}
g.next(6); // => Object {value: 12, done: true}
```

### Итерация

Генераторы можно обойти с помощью цикла `for of`:

```js
for (let i of gen()) {
	console.log(i); // выведет 1, а затем 2
}
```

### return

В конце функции генератора можно использовать `return`, например:

```js
function* gen() { 
    yield 1;
    yield 2;
    return 3;
}

// В этом случае, третий next() вернёт это значение
g.next(); // => Object {value: 3, done: true}
```

Однако, цикл `for of` по прежнему выведет только два значения.

## Генераторы и Промисы

```js
// Функция #1 возвращающая промис и делающая что-то...
function pr1(num) {
	return new Promise(res => {
        setTimeout(() => res(num * 2), 1000);
    });
}

// Функция #2 возвращающая промис и делающая что-то...
function pr2(num) {
	return new Promise(res => {
        setTimeout(() => res(num + 2), 2000);
    });
}

// Функция-генератор работающая с промисами в синхронном стиле
function* doSomething(startNum) {
	const value1 = yield pr1(startNum); // value1 === 4
    const value2 = yield pr2(value1);   // value2 === 6
    return value2;
}

// Вспомогательная функция
function execute(generator, yieldValue) {
	const next = generator.next(yieldValue);
    
    if (!next.done) {
    	next.value.then(res => execute(generator, res));
    } else {
    	console.log(`done with: ${next.value}`);
    }
}

execute(doSomething(2));
```

## Ссылки

* [Генераторы (learn.javascript.ru)](https://learn.javascript.ru/generator)
* [ES6 в деталях: Генераторы](http://frontender.info/es6-in-depth-generators/)
* [function* (MDN)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function*)
* [Generator (MDN)](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Generator)
