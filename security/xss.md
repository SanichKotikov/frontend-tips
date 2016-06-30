# Cross Site Scripting (XSS)

Тип атаки, заключающийся во внедрении и выполнении вредоносного кода в сайт/приложение через браузер пользователя, что бы обойти [SOP](sop.md).

Типичный пример уязвимости:

```js
document.write("Site is at: " + document.location.href);
```

Достаточно перейти по адресу:

```
site.com/action#<script>alert('xss')</script>ѕ
```

Основной вариант защиты — фильтровать все входящие данные (не доверять ни кому).

### Откуда можно "подхватить" эту заразу:

* `document.URL`
* `location`
* `window.name`
* `document.referrer`
* `localStorage`
* `cookies`

### Где можно выполнить:

* `eval`
* `document.write`
* `.innerHTML`
* `.src`
* `setTimeout / setInterval`
* `execScript`
