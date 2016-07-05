# target="_blank"

Страница, открытая через `target="_blank"`, получает частичный контроль над открывшей её страницей через js свойство `window.opener`.

Например, через `window.opener.location` мы можем сделать редирект на фишинговую страницу.

## Варианты решения

Самый простой — не использовать `target="_blank"` вообще. Пользователь достаточно опытный, что бы решать как открывать ссылки. Но если _требует бизнес_:

* `rel="noopener"` (не поддерживается FF, поэтому лучше использовать `rel="noopener noreferrer"`)
* Открывать через JS:   
```js
var newWnd = window.open();
newWnd.opener = null;
```

## Ссылки

* [Опасный target="_blank"](https://habrahabr.ru/post/282880/)
* [Target=”_blank” — the most underestimated vulnerability ever](https://medium.com/@jitbit/target-blank-the-most-underestimated-vulnerability-ever-96e328301f4c)
