---
title: Получить список складов WB
api: wb-work-with-products
method: GET
path: /api/v3/offices
operation_id: get-api-v3-offices
tags:
  - Склады продавца
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 5af6481102407edb
---

# Получить список складов WB

`GET /api/v3/offices`

Описание метода

Метод возвращает список складов WB для привязки к складу продавца при его [создании](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1warehouses/post) или [редактировании](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1warehouses~1%7BwarehouseId%7D/put).

Лимит запросов на один аккаунт продавца для всех методов складов продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Ответы

**200** — Успешно

- `address` — string. Адрес
- `cargoType` — integer (1, 3). Тип товара, который принимает склад: - `1` — малогабаритный товар (МГТ) - `3` — крупногабаритный товар (КГТ+)
- `city` — string. Город
- `deliveryType` — integer (1, 2, 3, 5, 6). Тип доставки, который принимает склад: - `1` — доставка на склад WB (FBS) - `2` — доставка силами продавца (DBS) - `3` — доставка курьером WB (DBW) - `5` — самовывоз (C&C) - `6` — экспресс-доставка силами продавца (ЕDBS)
- `federalDistrict` — string. Федеральный округ склада WB. Если `null`, склад находится за пределами РФ или федеральный округ не указан
- `id` — integer<int64>. ID
- `latitude` — number<float64>. Широта
- `longitude` — number<float64>. Долгота
- `name` — string. Название
- `selected` — boolean. Признак того, что склад уже выбран продавцом

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
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
