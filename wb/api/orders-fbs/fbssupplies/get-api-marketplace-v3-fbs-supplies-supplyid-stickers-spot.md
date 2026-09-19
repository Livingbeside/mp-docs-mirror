---
title: Получить QR-код СПОТ{{ /api/marketplace/v3/fbs/supplies/{supplyId}/stickers/spot }}
api: wb-orders-fbs
method: GET
path: /api/marketplace/v3/fbs/supplies/{supplyId}/stickers/spot
operation_id: getV3FbsSuppliesSupplyIdStickersSpot
tags:
  - fbsSupplies
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 19d543488fb99ba6
---

# Получить QR-код СПОТ{{ /api/marketplace/v3/fbs/supplies/{supplyId}/stickers/spot }}

`GET /api/marketplace/v3/fbs/supplies/{supplyId}/stickers/spot`

Описание метода

Метод возвращает сформированный QR-код СПОТ для поставки в формате PNG, кодировка base64.

Вы можете получить QR-код, когда в методе [получения данных СПОТ](./orders-fbs#tag/fbsSupplies/operation/postV3FbsSuppliesSpotList) будет признак `"status":"completed"`.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `supplyId` | path | string | да | ID поставки |

## Ответы

**200** — Успешно

- `qrCode` — string<base64> **обязательный**. QR-код поставки в кодировке base64

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `title` — string **обязательный**. Заголовок ошибки

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

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**404** — Не найдено

- `detail` — string **обязательный**. Детали ошибки
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
