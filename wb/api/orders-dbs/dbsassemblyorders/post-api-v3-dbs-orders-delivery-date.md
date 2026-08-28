---
title: Получить дату и время доставки
api: wb-orders-dbs
method: POST
path: /api/v3/dbs/orders/delivery-date
operation_id: postV3DbsOrdersDeliveryDate
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
deprecated: false
content_sha: 0068ea9dbc227227
---

# Получить дату и время доставки

`POST /api/v3/dbs/orders/delivery-date`

Описание метода

Метод возвращает информацию о выбранных покупателем дате и времени доставки заказов.

Лимит запросов на один аккаунт продавца для методов сборочных заданий DBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer]. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `orders` — array[object]
  - `dDate` — string. Актуальная дата доставки, указанная покупателем
  - `dDateFrom` — string. Не используется
  - `dDateOld` — string. Прежняя дата доставки. Доступна первые сутки после изменения
  - `dDateTo` — string. Не используется
  - `dTimeFrom` — string. Актуальное время доставки "с"
  - `dTimeFromOld` — string. Прежнее время доставки "с". Доступно первые сутки после изменения
  - `dTimeTo` — string. Актуальное время доставки "по"
  - `dTimeToOld` — string. Прежнее время доставки "по". Доступно первые сутки после изменения
  - `id` — integer. ID сборочного задания

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
