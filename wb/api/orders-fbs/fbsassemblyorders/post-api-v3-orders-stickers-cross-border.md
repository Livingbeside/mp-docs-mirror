---
title: Получить стикеры сборочных заданий трансграничных поставок
api: wb-orders-fbs
method: POST
path: /api/v3/orders/stickers/cross-border
operation_id: postV3OrdersStickersCrossBorder
tags:
  - fbsAssemblyOrders
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 41b24f948e4f384b
---

# Получить стикеры сборочных заданий трансграничных поставок

`POST /api/v3/orders/stickers/cross-border`

Описание метода

Метод возвращает список стикеров [сборочных заданий](./orders-fbs#tag/fbsAssemblyOrders/operation/getV3Orders) трансграничных поставок в формате PDF.

Для каждого сборочного задания в ответе указывается статус генерации стикера:
 - `awaitingTrackNumber` — стикер не готов. Ожидается трек-номер от перевозчика.
 - `ready` — стикер готов

 Стикер может генерироваться с задержкой. Повторяйте запрос, пока не получите статус ready.

Ограничения:
 - За один запрос можно получить максимум 100 стикеров.
 - Можно получить стикеры только для сборочных заданий, находящихся на сборке или в доставке — [статусы](./orders-fbs#tag/fbsAssemblyOrders/operation/postV3OrdersStatus) `confirm`, `complete`.

В песочнице этот метод всегда возвращает ответ 200.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer<int64>]. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `stickers` — array[object]
  - `orderId` — integer. ID сборочного задания
  - `status` — string (awaitingTrackNumber, ready). Статус генерации стикера: - `awaitingTrackNumber` — стикер не готов. Ожидается трек-номер от перевозчика. - `ready` — стикер готов
  - `parcelId` — string. Трек-номер в стикере для отслеживания сборочного задания
  - `file` — string<byte>. Стикер в формате PDF, кодировка base64
  - `partA` — string. Первая часть ID стикера для печати подписи
  - `partB` — string. Вторая часть ID стикера для печати подписи
  - `barcode` — string. Закодированное значение стикера

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
