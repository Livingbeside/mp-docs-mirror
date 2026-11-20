---
title: Формат данных запроса и ответа
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/data-format.md"
fetched_at: "2026-11-20T02:51:13Z"
content_sha: 1d260486566aa94e
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.71.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/push-notifications/concepts/data-format.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/data-format.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/push-notifications/concepts/data-format.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/data-format.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt?revision=r22204578
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt?revision=r22204578

# Формат данных запроса и ответа

В запросах Маркета к магазину используются только данные в формате JSON. Ответные данные от магазина должны быть представлены в том же формате.

Формат данных указывается в HTTP-заголовке `Content-Type: application/json`.

Требуемая кодировка запроса и ответа: UTF-8.


{% cut "Пример тела запроса" %}

```json translate=no
{
  "notificationType": "PING",
  "time": "2025-01-16T10:09:49.759084017Z"
}
```
{% endcut %}


{% cut "Пример тела ответа" %}

```json translate=no
{
  "version": "1.0.0",
  "name": "name",
  "time": "2025-01-16T10:09:49.759084017Z"
}
```
{% endcut %}

## Узнайте больше {#read-more}

[Описание формата JSON](http://json.org)
