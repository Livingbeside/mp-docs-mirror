---
title: Формат входных данных
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/input-format.md"
fetched_at: "2026-09-24T02:13:09Z"
content_sha: 0620222b12ea7986
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/input-format.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/input-format.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/input-format.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/concepts/input-format.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Формат входных данных

Входные структуры данных метода POST передаются в теле запроса.

Формат входных данных — JSON.

Формат входных данных указывается в HTTP-заголовке `Content-Type`: `application/json`.

Формат входных данных должен совпадать с [форматом ответа](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/result-format.md). Поэтому в заголовке `Content-Type` задавайте такой же формат, как и в заголовке `Accept` или в URL запроса (расширение `.json`).

Требуемая кодировка запроса: UTF-8.

Если в запросе не указан заголовок `Content-Type`, Маркет автоматически определяет формат данных. Сервис возвращает HTTP-статус `400 Bad Request` в следующих случаях:
- переданные данные невалидны;
- в структуре данных содержатся ошибки;
- в теле запроса используется неверная кодировка (отличная от UTF-8).

## Узнайте больше {#read-more}

[Описание формата JSON](http://json.org)
