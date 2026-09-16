---
title: Получить список складов WB
api: wb-item-management
method: GET
path: /api/v3/offices
operation_id: getV3Offices
tags:
  - sellerWarehouses
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 0deab0eacf22a1b5
---

# Получить список складов WB

`GET /api/v3/offices`

Описание метода

Метод возвращает список складов WB для привязки к складу продавца при его [создании](./item-management#tag/sellerWarehouses/operation/postV3Warehouses) или [редактировании](./item-management#tag/sellerWarehouses/operation/putV3WarehousesWarehouseId).

Лимит запросов на один аккаунт продавца для всех методов складов продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Ответы

**200** — Успешно

- `address` — string. Адрес
- `name` — string. Название
- `city` — string. Город
- `id` — integer<int64>. ID
- `longitude` — number<float64>. Долгота
- `latitude` — number<float64>. Широта
- `cargoType` — integer (1, 3). Тип товара, который принимает склад: - `1` — малогабаритный товар (МГТ) - `3` — крупногабаритный товар (КГТ+)
- `deliveryType` — integer (1, 2, 3, 5, 6). Тип доставки, который принимает склад: - `1` — доставка на склад WB (FBS) - `2` — доставка силами продавца (DBS) - `3` — Деливери WB (DBW) - `5` — самовывоз (C&C) - `6` — экспресс-доставка силами продавца (ЕDBS)
- `federalDistrict` — string. Федеральный округ склада WB. Если `null`, склад находится за пределами РФ или федеральный округ не указан
- `selected` — boolean. Признак того, что склад уже выбран продавцом

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**403** — Доступ запрещён

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
