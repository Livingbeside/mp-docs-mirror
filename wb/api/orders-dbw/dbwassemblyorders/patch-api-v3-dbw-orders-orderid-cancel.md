---
title: Отменить сборочное задание{{ /api/v3/dbw/orders/{orderId}/cancel }}
api: wb-orders-dbw
method: PATCH
path: /api/v3/dbw/orders/{orderId}/cancel
operation_id: patchV3DbwOrdersOrderIdCancel
tags:
  - dbwAssemblyOrders
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: 787a6f31dcbbde7d
---

# Отменить сборочное задание{{ /api/v3/dbw/orders/{orderId}/cancel }}

`PATCH /api/v3/dbw/orders/{orderId}/cancel`

Описание метода

Метод отменяет [сборочное задание](./orders-dbw#tag/dbwAssemblyOrders) и переводит в [статус](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersStatus) `cancel` — отменено продавцом.

Лимит запросов на один аккаунт продавца для методов DBW:

 получение и обновление списка контактов

 получение и удаление идентификаторов маркировки

 управление сборочными заданиями

 

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 300 запросов | 200 мс | 20 запросов |
| Сервисный | 1 мин | 300 запросов | 200 мс | 20 запросов |
| Базовый с секретом | 1 мин | 300 запросов | 200 мс | 20 запросов |
| Базовый | 1 ч | 10 запросов | 6 мин | 1 запрос |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `orderId` | path | integer<int64> | да | ID сборочного задания |

## Ответы

**204** — Отменено

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

**409** — Ошибка обновления статуса

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
