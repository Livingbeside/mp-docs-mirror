---
title: Заказы с информацией по клиенту{{ /api/v3/orders/client }}
api: wb-orders-fbs
method: POST
path: /api/v3/orders/client
operation_id: post-api-v3-orders-client
tags:
  - Сборочные задания FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: ee7f04c826aa7ff3
---

# Заказы с информацией по клиенту{{ /api/v3/orders/client }}

`POST /api/v3/orders/client`

Описание метода Метод позволяет получать информацию о покупателе по ID сборочного задания. Только для трансграничных поставок из **Турции**. Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса .

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
