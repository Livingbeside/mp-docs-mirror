---
title: Добавить сборочные задания к поставке{{ /api/marketplace/v3/supplies/{supplyId}/orders }}
api: wb-orders-fbs
method: PATCH
path: /api/marketplace/v3/supplies/{supplyId}/orders
operation_id: patch-api-marketplace-v3-supplies-supplyid-orders
tags:
  - Поставки FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 9fce3dfd360c46f0
---

# Добавить сборочные задания к поставке{{ /api/marketplace/v3/supplies/{supplyId}/orders }}

`PATCH /api/marketplace/v3/supplies/{supplyId}/orders`

Описание метода Метод добавляет до 100 [сборочных заданий](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders/get) к поставке и переводит их в [статус](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1status/post) `confirm` — на сборке. Может перемещать сборочные задания: - между активными поставками - из закрытой поставки в активную, если сборочные задания требуют [повторной отгрузки](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1supplies~1orders~1reshipment/get) В пустую поставку можно добавить сборочные задания любого габаритного типа. Поставка приобретает габаритный тип первого добавленного сборочного задания из поля cargoType . После этого в поставку можно добавить сборочные задания только того же габаритного типа, что и у поставки. В поставку нельзя добавить сборочные задания, поступившие на разные склады. В пустую поставку можно добавить сборочные задания трансграничных или внутренних поставок. После этого поставка приобретает тип первого добавленного сборочного задания из поля crossBorderType . Далее в неё можно добавить только сборочные задания такого же типа. Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса .

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `supplyId` | path | string | да | ID поставки |

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer]. ID сборочных заданий

## Ответы

**204** — Сборочные задания закреплены за поставкой

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

**409** — Ошибка добавления сборочного задания к поставке

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
