---
title: Получить дату и время доставки{{ /api/v3/dbs/orders/delivery-date }}
api: wb-orders-dbs
method: POST
path: /api/v3/dbs/orders/delivery-date
operation_id: postV3DbsOrdersDeliveryDate
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
deprecated: false
content_sha: 3cd9e723176629ce
---

# Получить дату и время доставки{{ /api/v3/dbs/orders/delivery-date }}

`POST /api/v3/dbs/orders/delivery-date`

Описание метода Метод возвращает информацию о выбранных покупателем дате и времени доставки заказов. Лимит запросов на один аккаунт продавца для методов сборочных заданий DBS : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса .

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer]. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `orders` — array[object]
  - `dTimeFrom` — string. Актуальное время доставки "с"
  - `dTimeTo` — string. Актуальное время доставки "по"
  - `dTimeFromOld` — string. Прежнее время доставки "с". Доступно первые сутки после изменения
  - `dTimeToOld` — string. Прежнее время доставки "по". Доступно первые сутки после изменения
  - `dDateOld` — string. Прежняя дата доставки. Доступна первые сутки после изменения
  - `dDate` — string. Актуальная дата доставки, указанная покупателем
  - `dDateFrom` — string. Не используется
  - `dDateTo` — string. Не используется
  - `id` — integer. ID сборочного задания

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
