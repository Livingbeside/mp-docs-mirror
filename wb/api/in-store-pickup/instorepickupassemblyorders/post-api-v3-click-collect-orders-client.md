---
title: Информация о покупателе
api: wb-in-store-pickup
method: POST
path: /api/v3/click-collect/orders/client
operation_id: postV3ClickCollectOrdersClient
tags:
  - inStorePickupAssemblyOrders
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: 95cc96d82f4e988b
---

# Информация о покупателе

`POST /api/v3/click-collect/orders/client`

Описание метода

Метод возвращает информацию о покупателе по ID сборочного задания.

Доступно только для сборочных заданий в статусах:
 - `confirm` — на сборке
 - `prepare` — готов к выдаче

Лимит запросов на один аккаунт продавца для методов сборочных заданий Самовывоз:

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
  - `firstName` — string. Имя покупателя
  - `orderID` — integer. ID сборочного задания
  - `phone` — string. Телефон для связи с покупателем. Чтобы связаться с покупателем наберите этот номер и введите добавочный код. Данный номер не является прямым номером покупателя
  - `phoneCode` — integer. Добавочный код

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные, обогащающие ошибку
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
- `data` — object. Дополнительные данные, обогащающие ошибку
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
