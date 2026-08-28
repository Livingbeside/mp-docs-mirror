---
title: Проверить, что заказ принадлежит покупателю
api: wb-in-store-pickup
method: POST
path: /api/v3/click-collect/orders/client/identity
operation_id: postV3ClickCollectOrdersClientIdentity
tags:
  - inStorePickupAssemblyOrders
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: a7114d5e65f144d6
---

# Проверить, что заказ принадлежит покупателю

`POST /api/v3/click-collect/orders/client/identity`

Описание метода

Метод сообщает, принадлежит ли проверяемый заказ покупателю или нет по переданному коду.

Доступно, если хотя бы одно сборочное задание из заказа находится в статусе prepare - готов к выдаче.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 30 запросов | 2 сек | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `orderCode` — string. Уникальный ID заказа покупателя
- `passcode` — string. Код подтверждения

## Ответы

**200** — Успешно

- `ok` — boolean. Принадлежит ли заказ покупателю: - `true` — принадлежит - `false` — значение не применяется. Если заказ не принадлежит покупателю, вы получите ответ со статус-кодом `409`

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные, обогащающие ошибку

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
- `data` — object. Дополнительные данные, обогащающие ошибку

**404** — Не найдено

- `code` — string
- `data` — object
- `message` — string

**409** — Введён неверный проверочный код

- `code` — string
- `data` — object
- `message` — string

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
