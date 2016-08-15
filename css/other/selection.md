# Стилизация выделенного текста с помощью `::selection`

```css
/* глобально */
::selection { background: yellow; }

/* только для p */
p::selection { color: red; }
```

Поддерживает всего три свойства:

* `color`
* `background` (`background-color`, `background-image`)
* `text-shadow`

Осторожно! `::selection` был удалён из спецификации.

## Ссылки

* [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/::selection)
* [caniuse](http://caniuse.com/#feat=css-selection)
* [css-tricks](https://css-tricks.com/almanac/selectors/s/selection/)
