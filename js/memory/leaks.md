# Утечки памяти

## Глобальная область

Глобальная область видимости всегда _достижима_, поэтому никогда не очищается из памяти. Соответственно, если есть необходимость хранить данные в глобальной области, о их удалении нужно заботиться самому (например через `= null`).

## Обработчики событий

Современные браузеры автоматически очищают обработчики событий для несуществующийх DOM элементов. Поэтому, использовать `removeEventListener` не обязательно. Но, например в IE6, этого не происходит.

## Таймеры

```js
var someResource = getData();
setInterval(function() {
    var node = document.getElementById('Node');
    if(node) {
        // Do stuff with node and someResource.
        node.innerHTML = JSON.stringify(someResource));
    }
}, 1000);
```

В какой то момент, элемент `node` может стать недоступным, но обработчик всё ещё есть и всё ещё ссылается на `someResource`.

## DOM

Если вы сохраняете ссылки на DOM элементы, например с помощью `getElementById`, не забывайте их очищать если элемента больше нет. Пример:

```js
var elements = {
    button: document.getElementById('button')
};
function removeButton() {
    document.body.removeChild(document.getElementById('button'));
    // В этой точне, у нас всё ещё есть ссылка на кнопку из глобального elements.
    // Другими словами, кнопка не будет удалена из памяти.
}
```

Если бы кнопка находилась в отдельном большом блоке, который в последствии удаляется, в памти остался бы весь этот блок, т.к. ссылка на его элемент всё ещё существует.

## Ссылки

* [4 Types of Memory Leaks in JavaScript and How to Get Rid Of Them](https://auth0.com/blog/2016/01/26/four-types-of-leaks-in-your-javascript-code-and-how-to-get-rid-of-them/)
