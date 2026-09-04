---
title: Получить список стран ОКСМ
api: wb-orders-fbs
method: GET
path: /api/marketplace/v3/fbs/dictionaries/countries/oksm
operation_id: getV3FbsDictionariesCountriesOksm
tags:
  - Поставки FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: a9acf5b3b4e99d9e
---

# Получить список стран ОКСМ

`GET /api/marketplace/v3/fbs/dictionaries/countries/oksm`

Описание метода

Метод возвращает список стран ОКСМ — Общероссийского классификатора стран мира — с полными названиями и кодами.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Ответы

**200** — Успешно

- `countries` — array[object] **обязательный**. Список стран ОКСМ
  - `code` — string **обязательный**. Код страны
  - `name` — string **обязательный**. Название страны

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
