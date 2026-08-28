---
title: Список чатов
api: wb-user-communication
method: GET
path: /api/v1/seller/chats
operation_id: getV1SellerChats
tags:
  - buyersChat
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: 1aaf07bf15cd0d33
---

# Список чатов

`GET /api/v1/seller/chats`

Описание метода

Метод возвращает список всех чатов продавца. По этим данным можно получить [события чатов](./user-communication#tag/buyersChat/operation/getV1SellerEvents) или [отправить сообщение покупателю](./user-communication#tag/buyersChat/operation/postV1SellerMessage).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Сервисный | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Базовый с секретом | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Ответы

**200** — Успешно

- `errors` — array[string]. Ошибки, если есть
- `result` — array[object]
  - `chatID` — string. ID чата
  - `clientName` — string. Имя покупателя
  - `goodCard` — object. Информация о заказе
    - `nmID` — integer. Артикул WB
    - `price` — integer. Фактическая цена с учетом всех скидок. Взимается с покупателя
    - `priceCurrency` — string. Валюта
    - `rid` — string. Уникальный ID заказа. Примечание: `rid` — это `srid` в ответах методов: - [Заявки покупателей на возврат](./user-communication#tag/buyersReturns/operation/getV1Claims) - [Лента заказов](./analytics#tag/orderFeed/operation/postV1OrderFeed) - [Заказы](./reports#tag/mainReports/operation/getV1SupplierOrders) - [Продажи](./reports#tag/mainReports/operation/getV1SupplierSales) - [Отчёт о возвратах и перемещении товаров](./reports#tag/returnsAndItemMovementReport) - [Детализации к отчётам реализации по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) - [Детализации к отчётам реализации за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed) - [Детализации к отчётам об издержках на приём платежей по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailedReportId) - [Детализации к отчётам об издержках на приём платежей за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailed)
    - `size` — string. Размер товара, соответствует `wbSize` в [карточке товара](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1list/post)
  - `lastMessage` — object. Последнее сообщение в чате
    - `addTimestamp` — integer. Время сообщения
    - `text` — string. Текст сообщения
  - `replySign` — string. Подпись чата. Требуется при [отправке сообщения](./user-communication#tag/buyersChat/operation/postV1SellerMessage)

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
