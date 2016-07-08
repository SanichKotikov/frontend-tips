# :focus-within

С помощью этого псевдо-класса можно оформлять элементы, внутри которых есть `input` с активным фокусом (`:focus`). Например, подсветить форму если есть фокус на одном из её полей.

```css
form:focus-within {
    box-shadow: 0 2px 3px rgba(0, 0, 0, .2);
}
```

## Ссылки

* [Живой пример на jsfiddle.net](https://jsfiddle.net/dhg3ep9e/)
* [drafts.csswg.org/the-focus-within-pseudo](https://drafts.csswg.org/selectors-4/#the-focus-within-pseudo)
