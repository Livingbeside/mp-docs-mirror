---
title: Формат данных
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/data-format.md"
fetched_at: "2026-09-04T01:59:39Z"
content_sha: 3ae475bb11b9fe67
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/push-notifications/concepts/data-format.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/data-format.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/push-notifications/concepts/data-format.md
  - href: ru/push-notifications/concepts/data-format.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

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
