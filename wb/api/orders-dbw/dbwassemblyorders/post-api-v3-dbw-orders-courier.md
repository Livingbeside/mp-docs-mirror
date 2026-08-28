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
content_sha: 75251966bcfa3a26
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
      - `pTimeFrom` — string<date-time>. Дата и время, с которого прибудет курьер
      - `pTimeTo` — string<date-time>. Дата и время, до которого прибудет курьер
      - `phone` — string. Номер телефона
    - `mustBeAssigned` — boolean. Должен ли быть назначен курьер к текущему моменту: - `false` — нет - `true` — да Если `"mustBeAssigned":true`, а `"contacts":null`, необходимо запросить контакты в [поддержке](https://seller.wildberries.ru/service-desk-v2)
    - `updatedAt` — string<date-time>. Дата и время обновления информации о курьере. Если `null`, информация не обновлялась
  - `orderID` — integer. ID сборочного задания

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
