---
title: Список чатов
api: wb-customer-communication
method: GET
path: /api/v1/seller/chats
operation_id: getV1SellerChats
tags:
  - buyersChat
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
deprecated: false
content_sha: 8c848fc33aa61909
---

# Список чатов

`GET /api/v1/seller/chats`

Описание метода

Метод возвращает список всех чатов продавца. По этим данным можно получить [события чатов](./customer-communication#tag/buyersChat/operation/getV1SellerEvents) или [отправить сообщение покупателю](./customer-communication#tag/buyersChat/operation/postV1SellerMessage).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Сервисный | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Базовый с секретом | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Ответы

**200** — Успешно

- `result` — array[object]
  - `chatID` — string. ID чата
  - `replySign` — string. Подпись чата. Требуется при [отправке сообщения](./customer-communication#tag/buyersChat/operation/postV1SellerMessage)
  - `clientName` — string. Имя покупателя
  - `goodCard` — object. Информация о заказе
    - `nmID` — integer. Артикул WB
    - `price` — integer. Фактическая цена с учетом всех скидок. Взимается с покупателя
    - `priceCurrency` — string. Валюта
    - `rid` — string. Уникальный ID заказа. Примечание: `rid` — это `srid` в ответах методов: - [Заявки покупателей на возврат](./customer-communication#tag/buyersReturns/operation/getV1Claims) - [Лента заказов](./analytics#tag/orderFeed/operation/postV1OrderFeed) - [Заказы](./reports#tag/mainReports/operation/getV1SupplierOrders) - [Продажи](./reports#tag/mainReports/operation/getV1SupplierSales) - [Отчёт о возвратах и перемещении товаров](./reports#tag/returnsAndItemMovementReport) - [Детализации к отчётам реализации по ID отчётов](./documents-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) - [Детализации к отчётам реализации за период](./documents-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed) - [Детализации к отчётам об издержках на приём платежей по ID отчётов](./documents-and-accounting#tag/financialReports/operation/postV1AcquiringDetailedReportId) - [Детализации к отчётам об издержках на приём платежей за период](./documents-and-accounting#tag/financialReports/operation/postV1AcquiringDetailed)
    - `size` — string. Размер товара, соответствует `wbSize` в [карточке товара](./item-management#tag/listings/operation/postV2GetCardsList)
  - `lastMessage` — object. Последнее сообщение в чате
    - `text` — string. Текст сообщения
    - `addTimestamp` — integer. Время сообщения
- `errors` — array[string]. Ошибки, если есть

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

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
