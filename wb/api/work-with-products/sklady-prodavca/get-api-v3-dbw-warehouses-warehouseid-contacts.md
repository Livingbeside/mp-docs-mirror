---
title: Список контактов{{ /api/v3/dbw/warehouses/{warehouseId}/contacts }}
api: wb-work-with-products
method: GET
path: /api/v3/dbw/warehouses/{warehouseId}/contacts
operation_id: get-api-v3-dbw-warehouses-warehouseid-contacts
tags:
  - Склады продавца
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 85f04f56a1c6b1a2
---

# Список контактов{{ /api/v3/dbw/warehouses/{warehouseId}/contacts }}

`GET /api/v3/dbw/warehouses/{warehouseId}/contacts`

Описание метода

Метод возвращает список контактов, привязанных к [складу продавца](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1warehouses/get).

Только для складов с типом доставки `3` — доставка курьером WB ([DBW](./orders-dbw)).

Лимит запросов на один аккаунт продавца для следующих методов DBW:

 получение и обновление списка контактов

 получение и удаление идентификаторов маркировки

 методы сборочных заданий

 

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `warehouseId` | path | integer<int64> | да | ID склада продавца |

## Ответы

**200** — Успешно

- `contacts` — array[object]
  - `comment` — string. Комментарий
  - `phone` — string. Номер телефона

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**402** — Требуется платёж

- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)
- `title` — string. Заголовок ошибки

**403** — Доступ запрещён

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
