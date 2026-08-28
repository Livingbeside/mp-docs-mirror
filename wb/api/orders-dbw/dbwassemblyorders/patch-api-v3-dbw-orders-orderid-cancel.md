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
content_sha: ca5212e4805d7c65
---

# Отменить сборочное задание{{ /api/v3/dbw/orders/{orderId}/cancel }}

`PATCH /api/v3/dbw/orders/{orderId}/cancel`

Описание метода Метод отменяет [сборочное задание](./orders-dbw#tag/dbwAssemblyOrders) и переводит в [статус](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersStatus) `cancel` — отменено продавцом. Лимит запросов на один аккаунт продавца для методов DBW: получение и обновление списка контактов получение и удаление идентификаторов маркировки управление сборочными заданиями | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 300 запросов | 200 мс | 20 запросов | | Сервисный | 1 мин | 300 запросов | 200 мс | 20 запросов | | Базовый с секретом | 1 мин | 300 запросов | 200 мс | 20 запросов | | Базовый | 1 ч | 10 запросов | 6 мин | 1 запрос | Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `orderId` | path | integer<int64> | да | ID сборочного задания |

## Ответы

**204** — Отменено

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

**409** — Ошибка обновления статуса

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
