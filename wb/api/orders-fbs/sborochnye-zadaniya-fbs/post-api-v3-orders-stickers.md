---
title: Получить стикеры сборочных заданий
api: wb-orders-fbs
method: POST
path: /api/v3/orders/stickers
operation_id: post-api-v3-orders-stickers
tags:
  - Сборочные задания FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 725ff428767d48bf
---

# Получить стикеры сборочных заданий

`POST /api/v3/orders/stickers`

Описание метода

Метод возвращает список стикеров для [сборочных заданий](./orders-fbs#tag/Sborochnye-zadaniya-FBS) в [статусах](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1status/post) `confirm` — на сборке и `complete` — в доставке. 

Если за сборочным заданием не закреплён обязательный [номер декларации на товары (ДТ)](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1%7BorderId%7D~1meta~1customs-declaration/put), получить стикеры для этого сборочного задания невозможно.

За один запрос можно получить максимум 100 стикеров. 

Можно получить стикер в форматах:
 - SVG
 - ZPLV (вертикальный)
 - ZPLH (горизонтальный)
 - PNG

Доступны размеры:
 - 580x400 px при `width=58&height=40` в запросе
 - 400x300 px при `width=40&height=30` в запросе

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

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
  - `barcode` — string. Закодированное значение стикера
  - `file` — string. Полное представление стикера в заданном формате
  - `orderId` — integer<int64>. ID сборочного задания
  - `partA` — string. Первая часть ID стикера для печати подписи
  - `partB` — string. Вторая часть ID стикера для печати подписи

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

**409** — Конфликт

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
