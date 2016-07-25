# CSS Containment

Позволяет изолировать такие операции как `layout` и `paint`, для серьёзной оптимизации рендеринга.

```
contain: none | strict | content | [ size || layout || style || paint ];
```

Рассмотрим следующий пример: [jsfiddle.net/jsL7w69d/](https://jsfiddle.net/jsL7w69d/).

Не смотря на то, что изменения внутри `.content` никак не влияют на окружение, браузер всё равно делает `layout` всего документа (`Layout root: #document`). К тому же, происходит `repaint` левого блока `.aside`.

Раскоментриуем строчку `contain: layout size;` и сравним результат. Теперь `repaint` и `layout` происходит исключительно внутри блока `.content` (`Layout root: div.content`). Даже на таком простом примере, с указанным `contain`, `layout` отрабатывает, приблизительно, в два раза быстрее (результат может отличаться, в зависимости от платформы и браузера).

## Ссылки

* [CSS Containment Module Level 3](https://drafts.csswg.org/css-containment/)
* [CSS Containment in Chrome 52](https://developers.google.com/web/updates/2016/06/css-containment)
