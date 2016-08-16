# CSS переменные (кастомные свойства)

Это не просто переменные, это кастомные свойства которые работают в рантайме по основным принципам CSS, таким как каскад и наследование. С их помощью, например, можно контролировать процесс загрузки/рендера страницы (см. _Control CSS loading with custom properties_ ниже).

## Базовый синтаксис

```css
/* инициализация */
:root {
    --main-bg-color: brown;
}

/* использование */
element {
  background-color: var(--main-bg-color);
}
```

## Ссылки

* [Using CSS variables (MDN)](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables)
* [caniuse](http://caniuse.com/#feat=css-variables)
* [W3C](https://drafts.csswg.org/css-variables/)
* [Control CSS loading with custom properties](https://jakearchibald.com/2016/css-loading-with-custom-props/)
* [PostCSS плагин](https://github.com/postcss/postcss-custom-properties)
