---
title: Информация о покупателе{{ /api/v3/dbs/orders/client }}
api: wb-orders-dbs
method: POST
path: /api/v3/dbs/orders/client
operation_id: postV3DbsOrdersClient
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
deprecated: false
content_sha: 17da5142f21ead3b
---

# Информация о покупателе{{ /api/v3/dbs/orders/client }}

`POST /api/v3/dbs/orders/client`

Описание метода Метод возвращает информацию о покупателе по ID сборочных заданий. Лимит запросов на один аккаунт продавца для методов сборочных заданий DBS : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса .

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer]. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `orders` — array[object]. Информация о покупателе
  - `replacementPhone` — string. Подменный номер для связи с покупателем. Пустое значение `""` указывает, что номер еще не назначен
  - `firstName` — string. Имя покупателя
  - `fullName` — string. Полное имя, используется для оформления документов. Например, документы на автомобиль
  - `orderID` — integer. ID сборочного задания
  - `phone` — string. Резервный подменный номер телефона для связи с покупателем. Используйте, если недоступен основной номер из `replacementPhone`. Чтобы позвонить покупателю, наберите этот номер и добавочный код из `phoneCode`. Пустое значение `""` указывает, что номер ещё не назначен
  - `phoneCode` — integer. Добавочный код. Пустое значение `""` указывает, что код ещё не назначен
  - `additionalPhoneCodes` — array[string]. Дополнительные добавочные коды. Используйте, если не получилось дозвониться по добавочному коду из `phoneCode`. Пустое значение `""` указывает, что код ещё не назначен

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
