---
title: Получить стикеры для сборочных заданий с доставкой в ПВЗ
api: wb-orders-dbs
method: POST
path: /api/marketplace/v3/dbs/orders/stickers
operation_id: postV3DbsOrdersStickers
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
deprecated: false
content_sha: f2ac7e2a8eadcdcf
---

# Получить стикеры для сборочных заданий с доставкой в ПВЗ

`POST /api/marketplace/v3/dbs/orders/stickers`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену, 
 Базовому токену с секретом

Метод возвращает стикеры для сборочных заданий с доставкой в ПВЗ в [статусах](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusInfo):
 - `confirm` — на сборке
 - `deliver` — в доставке

Получить стикеры можно только в размере 580x400 px в формате PDF.

Лимит запросов на один аккаунт продавца для методов сборочных заданий DBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

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
  - `barcode` — string **обязательный**. Закодированное значение стикера
  - `file` — string **обязательный**. Полное представление стикера, кодировка base64
  - `orderId` — integer<int64> **обязательный**. ID сборочного задания
  - `partA` — string **обязательный**. Первая часть ID стикера
  - `partB` — string **обязательный**. Вторая часть ID стикера

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
