# Кастомные события (CustomEvent)

С помощью конструктора _CustomEvent_ можно создать своё (нестандартное) событие.

```js
const event = new CustomEvent(typeArg, customEventInit);
```

* _typeArg_ — строка с названием события;
* _customEventInit_ — объект с единственным свойством _detail_, в которое можно записать любую,
  связанную с событием, информацию.

Для вызова события используется специальный метод `elem.dispatchEvent(event);`,
где _elem_ — DOM элемент который будет записан в _Event.target_, а _event_ — объект события.

Простой пример:

```js
elem.addEventListener('hello', event => {
    console.info(event.detail.name); // => Вася
}, false);

const event = new CustomEvent('hello', { detail: { name: 'Вася' } });

elem.dispatchEvent(event);
```

## Совместимость

Конструктор _CustomEvent_ достаточно хорошо поддерживается. Однако для IE9-11,
Mobile IE 10-11 и Android 3-4.3 придётся использовать старый синтаксис (полифил).

## Ссылки

* [CustomEvent (W3C)](https://www.w3.org/TR/dom/#interface-customevent)
* [CustomEvent (caniuse)](http://caniuse.com/#feat=customevent)
