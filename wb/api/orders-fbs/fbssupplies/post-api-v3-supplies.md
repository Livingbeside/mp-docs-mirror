---
title: Создать новую поставку
api: wb-orders-fbs
method: POST
path: /api/v3/supplies
operation_id: postV3Supplies
tags:
  - fbsSupplies
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: dd6c1486639605ff
---

# Создать новую поставку

`POST /api/v3/supplies`

Описание метода

Метод создаёт новую [поставку](./orders-fbs#tag/fbsSupplies/operation/getV3SuppliesSupplyId).

Ограничения:
- Только для [сборочных заданий](./orders-fbs#tag/fbsAssemblyOrders/operation/getV3Orders) по модели FBS.
- При добавлении в поставку все передаваемые сборочные задания в [статусе](./orders-fbs#tag/fbsAssemblyOrders/operation/postV3OrdersStatus) `new` будут автоматически переведены в статус `confirm` — на сборке.
- Если вы переведёте сборочное задание в статус `cancel` — отмена продавцом, прикрепленное сборочное задание автоматически удалится из поставки.
- Поставку можно собрать только из сборочных заданий (заказов) одного габаритного типа `cargoType`. Новая поставка не обладает габаритным признаком, она приобретает габаритный признак первого заказа, добавленного в поставку.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `name` — string. Наименование поставки

## Ответы

**201** — Создано

- `id` — string. ID поставки

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
