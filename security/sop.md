# Same origin policy (SOP)

Основная модель безопасности в современных браузерах, которая не позволяют сценариям обращаться к данным, расположенным на сторонних доменах.

Домены считаются одинаковыми, если у них одинаковые:

* протокол (`http`)
* домен (`site.com`)
* порт (`80`)

## Cross-Origin Resource Sharing (CORS)

Механизм который позволяет (специально) обойти эту защиту.   
[HTTP access control (CORS)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS)
