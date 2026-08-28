---
title: Информация о курьере
api: wb-orders-dbw
method: POST
path: /api/v3/dbw/orders/courier
operation_id: postV3DbwOrdersCourier
tags:
  - dbwAssemblyOrders
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: d63b4375fcf6e7e3
---

# Информация о курьере

`POST /api/v3/dbw/orders/courier`

Описание метода

Метод возвращает контактные данные и номер автомобиля курьера по ID сборочного задания. 
 Для сборочных заданий в статусах `confirm`, `complete`.

Лимит запросов на один аккаунт продавца для следующих методов DBW:

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

- `orders` — array[object]
  - `courierInfo` — object. Информация о курьере
    - `contacts` — object. Контактные данные курьера
      - `carNumber` — string. Номер автомобиля
      - `fullName` — string. ФИО курьера
      - `phone` — string. Номер телефона
      - `pTimeFrom` — string<date-time>. Дата и время, с которого прибудет курьер
      - `pTimeTo` — string<date-time>. Дата и время, до которого прибудет курьер
    - `mustBeAssigned` — boolean. Должен ли быть назначен курьер к текущему моменту: - `false` — нет - `true` — да Если `"mustBeAssigned":true`, а `"contacts":null`, необходимо запросить контакты в [поддержке](https://seller.wildberries.ru/service-desk-v2)
    - `updatedAt` — string<date-time>. Дата и время обновления информации о курьере. Если `null`, информация не обновлялась
  - `orderID` — integer. ID сборочного задания

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
