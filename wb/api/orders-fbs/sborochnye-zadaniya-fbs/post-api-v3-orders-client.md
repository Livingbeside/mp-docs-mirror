---
title: Заказы с информацией по клиенту
api: wb-orders-fbs
method: POST
path: /api/v3/orders/client
operation_id: post-api-v3-orders-client
tags:
  - Сборочные задания FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 84ed2521ec0e8741
---

# Заказы с информацией по клиенту

`POST /api/v3/orders/client`

Описание метода

Метод позволяет получать информацию о покупателе по ID сборочного задания.

Только для трансграничных поставок из **Турции**.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer]. Список заказов

## Ответы

**200** — Успешно

- `orders` — array[object]. Информация по клиенту для трансграничных поставок из Турции
  - `firstName` — string. Имя клиента
  - `fullName` — string. Фамилия, Имя, Отчество
  - `lastName` — string. Фамилия клиента
  - `middleName` — string. Отчество клиента
  - `orderID` — integer. Номер заказа
  - `phone` — string. Телефон для связи с клиентом
  - `phoneCode` — string. Не используется

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
