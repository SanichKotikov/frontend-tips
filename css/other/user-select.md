# user-select

Позволяет указать, какие елементы могут быть выделены и как.

`user-select: none` запрещает выделение. Может быть полезно при создании приложений, в которых не должен выделяться текст интерфейса. Например, по _случайному_ двойному клику.

`user-select: all` клик по элементу, или одному из его потомков, автоматически выделит всё в этой области.

Есть и другие значения: `auto`, `text` и `contain`, но не все они поддерживаются браузерами.

## Проблемы

Значение `user-select: none` ломает выделение `input` элементов в iOS Safari.

## Ссылки

* [Controlling content selection](https://drafts.csswg.org/css-ui-4/#content-selection)
* [caniuse.com/user-select](http://caniuse.com/#search=user-select)
* [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/user-select)
