# Обзор (event loop, stack and queue)

JavaScript однопоточный! Это означает, что в одну еденицу времени выполняется что-то одно.
Нужно также понимать, что этот поток блокирует браузер (отрисовку и взаимодействие со страницей).
Поэтому большие вычесления лучше делать через `Web Worker`, у которого свой отдельный поток.

## Определения:

### Стек (stack)

Вызов функции создаёт _контекст выполнения_. Вызов вложенной функции создаёт новый контекст,
а старый сохраняется в **Стек**:

```js
function first() {
    const err = new Error();
    console.log(err.stack);
    /* =>
        at first — текущее положение
        at second
        at window.onload
    */
}

function second() {
	first();
}

second();
```

### Очередь событий (queue)

Очередь колбеков, которые будут выполнены, как только стек будет пуст.

### Куча (heap)

Неструктурированная область памяти, где хранятся объекты.

## Как это всё работает вместе?

```

----------------     -------------------
|      |       |     | WebAPIs:        |
| heap | stack | ==> | XHR, setTimeout |
|      |       |     | ...             |
----------------     -------------------
       ▲
----------------              |
|  event loop  |              ▼
----------------
       ▲
----------------------------------------
|               queue                  |
----------------------------------------

```

Что тут важно понимать:

* `WebAPIs` не блокируют основной поток (за некоторыми исключениями), и выполняются браузером отдельно.
  Как только они выполнятся, `callback` отправляется в очередь (`queue`);
* Как только `stack` освободится, `event loop` извлекает первый `callback` из очереди и помещает в стек,
  где он и выполняется;
* Как только `stack` снова освободится, `event loop` извлекает следующий `callback` и т.д.;
* Если очередь пуста — `event loop` ждёт, пока в неё что ни будь попадёт.

Простой пример:

```js
console.log(1);
setTimeout(() => console.log(2), 5);
const endDate = Date.now() + 10;
while (Date.now() < endDate){
	// busy loop for 10 ms
}
console.log(3);
```

В консоль будет выведено:

```
1
3
2
```

Не смотря на таймер в `5ms`, `event loop` не может перенести _задачу_ из очереди (и выполнить её),
т.к. основной поток всё ещё занят. В итоге, таймаут выполнится не раньше, чем через `10ms`.

## Одна итерация (tick)

Одна итерация `event loop` называется `tick`, и она выполняет какую-то одну задачу (`task`) из очереди.

TODO: notes:
* один тик выполняет один такс из очереди (очередей?), микротаски и рендер (applyScrollResizeAndCSS > runAnimationFrames > render)
* в одном event loop может быть несколько очередей
* whereas all windows on the same origin share an event loop as they can synchronously communicate
* An event loop has multiple task sources which guarantees execution order within that source (specs such as IndexedDB define their own), but the browser gets to pick which source to take a task from on each turn of the loop. This allows the browser to give preference to performance sensitive tasks such as user-input.
* Between tasks, the browser _may_ render updates. (т.е. requestAnimationFrame может и не вызваться)

https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/

## Ссылки:

* [Philip Roberts: What the heck is the event loop anyway?](https://www.youtube.com/watch?v=8aGhZQkoFbQ)
* [Writing a JavaScript framework - Execution timing, beyond setTimeout](https://blog.risingstack.com/writing-a-javascript-framework-execution-timing-beyond-settimeout/)
