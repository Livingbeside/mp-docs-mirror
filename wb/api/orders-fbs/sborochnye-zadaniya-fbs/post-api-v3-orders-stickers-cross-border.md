---
title: Получить стикеры сборочных заданий трансграничных поставок
api: wb-orders-fbs
method: POST
path: /api/v3/orders/stickers/cross-border
operation_id: post-api-v3-orders-stickers-cross-border
tags:
  - Сборочные задания FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 56a8fadbaff7c04a
---

# Получить стикеры сборочных заданий трансграничных поставок

`POST /api/v3/orders/stickers/cross-border`

Описание метода

Метод возвращает список стикеров [сборочных заданий](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders/get) трансграничных поставок в формате PDF.

Для каждого сборочного задания в ответе указывается статус генерации стикера:
 - `awaitingTrackNumber` — стикер не готов. Ожидается трек-номер от перевозчика.
 - `ready` — стикер готов

 Стикер может генерироваться с задержкой. Повторяйте запрос, пока не получите статус ready.

Ограничения:
 - За один запрос можно получить максимум 100 стикеров.
 - Можно получить стикеры только для сборочных заданий, находящихся на сборке или в доставке — [статусы](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1status/post) `confirm`, `complete`.

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
  - `barcode` — string. Закодированное значение стикера
  - `file` — string<byte>. Стикер в формате PDF, кодировка base64
  - `orderId` — integer. ID сборочного задания
  - `parcelId` — string. Трек-номер в стикере для отслеживания сборочного задания
  - `partA` — string. Первая часть ID стикера для печати подписи
  - `partB` — string. Вторая часть ID стикера для печати подписи
  - `status` — string (awaitingTrackNumber, ready). Статус генерации стикера: - `awaitingTrackNumber` — стикер не готов. Ожидается трек-номер от перевозчика. - `ready` — стикер готов

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
