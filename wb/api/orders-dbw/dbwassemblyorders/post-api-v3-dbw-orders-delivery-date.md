---
title: Получить дату и время доставки
api: wb-orders-dbw
method: POST
path: /api/v3/dbw/orders/delivery-date
operation_id: postV3DbwOrdersDeliveryDate
tags:
  - dbwAssemblyOrders
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: 47949405e5b8a9b3
---

# Получить дату и время доставки

`POST /api/v3/dbw/orders/delivery-date`

Описание метода

Метод возвращает информацию о выбранных покупателем дате и времени доставки сборочных заданий.

Лимит запросов на один профиль продавца для следующих методов DBW:

 получение и обновление списка контактов

 получение и удаление идентификаторов маркировки

 методы сборочных заданий

 

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer]. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `orders` — array[object] **обязательный**
  - `dTimeFrom` — string **обязательный**. Актуальное время доставки "с"
  - `dTimeTo` — string **обязательный**. Актуальное время доставки "по"
  - `dTimeFromOld` — string **обязательный**. Прежнее время доставки "с". Доступно первые сутки после изменения
  - `dTimeToOld` — string **обязательный**. Прежнее время доставки "по". Доступно первые сутки после изменения
  - `dDateOld` — string **обязательный**. Прежняя дата доставки. Доступна первые сутки после изменения
  - `dDate` — string **обязательный**. Актуальная дата доставки
  - `id` — integer **обязательный**. ID сборочного задания

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
