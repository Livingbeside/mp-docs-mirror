---
title: Получить стикеры для сборочных заданий с доставкой в ПВЗ{{ /api/marketplace/v3/dbs/orders/stickers }}
api: wb-orders-dbs
method: POST
path: /api/marketplace/v3/dbs/orders/stickers
operation_id: postV3DbsOrdersStickers
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
deprecated: false
content_sha: bc4b7f129dca77cc
---

# Получить стикеры для сборочных заданий с доставкой в ПВЗ{{ /api/marketplace/v3/dbs/orders/stickers }}

`POST /api/marketplace/v3/dbs/orders/stickers`

Описание метода Метод доступен по Персональному токену, Сервисному токену, Базовому токену с секретом Метод возвращает стикеры для сборочных заданий с доставкой в ПВЗ в [статусах](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusInfo): - `confirm` — на сборке - `deliver` — в доставке Получить стикеры можно только в размере 580x400 px в формате PDF. Лимит запросов на один аккаунт продавца для методов сборочных заданий DBS : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `type` | query | string (pdf) | да | Формат стикера |
| `width` | query | integer (58) | да | Ширина стикера |
| `height` | query | integer (40) | да | Высота стикера |

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer<int64>] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `stickers` — array[object]. Стикеры
  - `orderId` — integer<int64> **обязательный**. ID сборочного задания
  - `partA` — string **обязательный**. Первая часть ID стикера
  - `partB` — string **обязательный**. Вторая часть ID стикера
  - `barcode` — string **обязательный**. Закодированное значение стикера
  - `file` — string **обязательный**. Полное представление стикера, кодировка base64

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**402** — Требуется платёж

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)

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
