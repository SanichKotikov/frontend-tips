# Замыкание и область видимости

## Лексическое окружение

При запуске функции создаётся объект `LexicalEnvironment`, в который записываются аргументы, функции и переменные, определённяе внутри этой самой функции.

```js
function fn(prop) {
    // [[LexicalEnvironment]] = { prop, something }
    var something = 'something';
}
```

При доступе к переменной, сначала она ищется в `LexicalEnvironment`, а затем во внешнем окружении через скрытое свойство `[[Scope]]`, которое ссылается на лексическое окружение, в котором была создана функция.

```js
fn.[[Scope]] = LexicalEnvironment текущего запуска fn
```

**Замыкание** (closure) — это функция + внешние переменные. Другими словами: `LexicalEnvironment` + `[[Scope]]`.

## Исключение

При создании функции с использованием `new Function`, её свойство `[[Scope]]` ссылается не на текущий `LexicalEnvironment`, а на глобальный (window).

```js
const a = 1;

function fn() {
  const a = 2;
  return new Function('', 'alert(a)');
}

fn()(); // => 1
```
