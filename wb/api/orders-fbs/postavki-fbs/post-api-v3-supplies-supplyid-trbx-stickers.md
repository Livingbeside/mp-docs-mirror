---
title: Получить стикеры грузомест поставки{{ /api/v3/supplies/{supplyId}/trbx/stickers }}
api: wb-orders-fbs
method: POST
path: /api/v3/supplies/{supplyId}/trbx/stickers
operation_id: post-api-v3-supplies-supplyid-trbx-stickers
tags:
  - Поставки FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 1037553bd7a93e6a
---

# Получить стикеры грузомест поставки{{ /api/v3/supplies/{supplyId}/trbx/stickers }}

`POST /api/v3/supplies/{supplyId}/trbx/stickers`

Описание метода

Метод возвращает QR-стикеры в форматах:
 - SVG
 - ZPLV (вертикальный)
 - ZPLH (горизонтальный)
 - PNG

Размер стикеров — 580x400 px.

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

## Запрос

**Тело запроса** (`application/json`):

- `trbxIds` — array[string] **обязательный**. Список ID грузомест, по которым необходимо вернуть стикеры

## Ответы

**200** — Успешно

- `stickers` — array[object]
  - `barcode` — string. Закодированное значение стикера
  - `file` — string<byte>. Полное представление стикера в заданном формате (кодировка base64)

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

**404** — Не найдено

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
