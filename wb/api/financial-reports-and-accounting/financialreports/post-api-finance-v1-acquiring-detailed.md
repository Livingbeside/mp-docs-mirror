---
title: Детализации к отчётам об издержках на приём платежей за период
api: wb-financial-reports-and-accounting
method: POST
path: /api/finance/v1/acquiring/detailed
operation_id: postV1AcquiringDetailed
tags:
  - financialReports
spec_version: finances
source: "https://dev.wildberries.ru/docs/openapi/financial-reports-and-accounting"
deprecated: false
content_sha: cf78640af73566a5
---

# Детализации к отчётам об издержках на приём платежей за период

`POST /api/finance/v1/acquiring/detailed`

Описание метода

 Метод доступен по
 Персональному токену, 
 Сервисному токену

Метод возвращает детализации к [отчётам об издержках на приём платежей](https://seller.wildberries.ru/suppliers-mutual-settlements/reports-implementations/acquiring-reports) за указанный период.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1 запрос | 1 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `dateFrom` — string **обязательный**. Начальная дата отчёта. Можно передать дату или дату со временем. Время можно указывать с точностью до секунд или миллисекунд. Дата передаётся в формате [RFC3339](https://datatracker.ietf.org/doc/html/rfc3339), время — в часовом поясе Москва `UTC+3`. Примеры: - `2025-06-20` - `2025-06-20T23:59:59` - `2025-06-20T00:00:00.12345` - `2025-06-20T00:00:00`
- `dateTo` — string **обязательный**. Конечная дата отчёта. Дата в формате [RFC3339](https://datatracker.ietf.org/doc/html/rfc3339). Можно передать дату или дату со временем. Время можно указывать с точностью до секунд или миллисекунд. Время передаётся в часовом поясе Москва `UTC+3`. Примеры: - `2025-06-20` - `2025-06-20T23:59:59` - `2025-06-20T00:00:00.12345` - `2025-06-20T00:00:00`
- `fields` — array[string]. Список полей, которые вернутся в ответе. Если параметр не указан, возвращаются все поля
- `limit` — integer. Количество строк в ответе По умолчанию: `100000`.
- `rrdId` — integer. ID строки ответа. Необходим для получения отчёта частями. Начинайте загрузку отчёта с `"rrdid":0`. В последующих запросах передавайте значение `rrdId` из последней строки предыдущего ответа. Повторяйте запрос, пока не получите ответ `204` По умолчанию: `0`.

## Ответы

**200** — Успешно

- `acqDate` — string **обязательный**. Дата операции
- `acquiringBank` — string **обязательный**. Наименование банка-эквайера
- `acquiringFee` — string **обязательный**. Размер комиссии за эквайринг, в том числе НДС
- `acquiringFeeVat` — string **обязательный**. Сумма НДС
- `currency` — string **обязательный**. Валюта отчёта
- `docTypeName` — string **обязательный**. Тип документа
- `invoiceDate` — string **обязательный**. Дата счёта-фактуры
- `invoiceNumber` — string **обязательный**. Номер счёта-фактуры
- `nmId` — integer **обязательный**. Артикул WB
- `reportId` — integer<int64> **обязательный**. ID отчёта
- `retailAmount` — string **обязательный**. Вайлдберриз реализовал Товар (Пр)
- `rrdId` — integer **обязательный**. ID строки
- `saleDate` — string **обязательный**. Дата продажи
- `shkId` — integer **обязательный**. Штрихкод
- `srid` — string **обязательный**. ID заказа. В ответах методов сборочных заданий [FBS](./orders-fbs#tag/Sborochnye-zadaniya-FBS), [DBW](./orders-dbw#tag/dbwAssemblyOrders), [DBS](./orders-dbs#tag/dbsAssemblyOrders) и [Самовывоз](./in-store-pickup#tag/inStorePickupAssemblyOrders) `srid` равен `rid`
- `taxRegistrationReasonCode` — string **обязательный**. КПП
- `tin` — string **обязательный**. ИНН

**204** — Нет данных

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. ID запроса
- `status` — integer. HTTP статус-код
- `title` — string. Заголовок ошибки

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

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
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
