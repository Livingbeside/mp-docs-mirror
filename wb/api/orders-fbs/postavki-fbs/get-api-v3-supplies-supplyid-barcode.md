---
title: Получить QR-код поставки{{ /api/v3/supplies/{supplyId}/barcode }}
api: wb-orders-fbs
method: GET
path: /api/v3/supplies/{supplyId}/barcode
operation_id: get-api-v3-supplies-supplyid-barcode
tags:
  - Поставки FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 8e03b1399a621216
---

# Получить QR-код поставки{{ /api/v3/supplies/{supplyId}/barcode }}

`GET /api/v3/supplies/{supplyId}/barcode`

Описание метода

Метод возвращает QR-код [поставки](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D/get) в форматах:
 - SVG
 - ZPLV (вертикальный)
 - ZPLH (горизонтальный)
 - PNG

QR-код поставки можно получить, только если поставка [передана в доставку](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D~1deliver/patch).

Размер — 580x400 px.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `supplyId` | path | string | да | ID поставки |
| `type` | query | string (svg, zplv, zplh, png) | да | Тип стикера |

## Ответы

**200** — Успешно

- `barcode` — string. Закодированное значение стикера (ID поставки)
- `file` — string<byte>. Полное представление стикера в заданном формате (кодировка base64)

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

**404** — Не найдено

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**409** — Ошибка запроса данных

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
