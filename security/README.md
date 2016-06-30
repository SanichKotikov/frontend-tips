# Безопасность

Этот раздел относится не только к клиентской части, но и к серверной.

* [Same Origin Policy](sop.md)
* [Cross Site Scripting (XSS)](xss.md)
* [Cross Site Request Forgery (XSRF/CSRF)](xsrf.md)
* [JSON Hijacking](json-hijacking.md)
* [Заголовки](headers.md)

Помимо перечисленного стоит также отметить, что нужно всегда проверять даные (содержимое и источник) приходящие через `Web Sockets`, `Window.postMessage()` и подобные вещи.
