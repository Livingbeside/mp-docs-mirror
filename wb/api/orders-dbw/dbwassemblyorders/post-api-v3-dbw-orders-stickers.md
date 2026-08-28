---
title: Получить стикеры сборочных заданий{{ /api/v3/dbw/orders/stickers }}
api: wb-orders-dbw
method: POST
path: /api/v3/dbw/orders/stickers
operation_id: postV3DbwOrdersStickers
tags:
  - dbwAssemblyOrders
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: 25c622f6e944abe5
---

# Получить стикеры сборочных заданий{{ /api/v3/dbw/orders/stickers }}

`POST /api/v3/dbw/orders/stickers`

Описание метода Метод возвращает список стикеров для [сборочных заданий](./orders-dbw#tag/dbwAssemblyOrders/operation/getV3DbwOrdersNew) в [статусах](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersStatus): - `confirm` — на сборке - `complete` — в доставке За один запрос можно получить максимум 100 стикеров. Доступные форматы стикеров: - SVG - ZPLV (вертикальный) - ZPLH (горизонтальный) - PNG Доступны размеры: - 580x400 px при `width=58&height=40` в запросе - 400x300 px при `width=40&height=30` в запросе Лимит запросов на один аккаунт продавца для следующих методов DBW: получение и обновление списка контактов получение и удаление идентификаторов маркировки методы сборочных заданий | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `type` | query | string (svg, zplv, zplh, png) | да | Тип стикера |
| `width` | query | integer (58, 40) | да | Ширина стикера |
| `height` | query | integer (40, 30) | да | Высота стикера |

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer<int64>]. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `stickers` — array[object]
  - `orderId` — integer<int64>. ID сборочного задания
  - `partA` — string. Первая часть ID стикера для печати подписи
  - `partB` — string. Вторая часть ID стикера для печати подписи
  - `barcode` — string. Закодированное значение стикера
  - `file` — string. Полное представление стикера в заданном формате (кодировка base64)

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
