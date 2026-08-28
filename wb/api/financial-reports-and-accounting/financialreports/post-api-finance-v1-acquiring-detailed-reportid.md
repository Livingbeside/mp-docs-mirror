---
title: Детализации к отчётам об издержках на приём платежей по ID отчётов{{ /api/finance/v1/acquiring/detailed/{reportId} }}
api: wb-financial-reports-and-accounting
method: POST
path: /api/finance/v1/acquiring/detailed/{reportId}
operation_id: postV1AcquiringDetailedReportId
tags:
  - financialReports
spec_version: finances
source: "https://dev.wildberries.ru/docs/openapi/financial-reports-and-accounting"
deprecated: false
content_sha: ddc47f75021b28e9
---

# Детализации к отчётам об издержках на приём платежей по ID отчётов{{ /api/finance/v1/acquiring/detailed/{reportId} }}

`POST /api/finance/v1/acquiring/detailed/{reportId}`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену

Метод возвращает детализации к [отчётам об издержках на приём платежей](https://seller.wildberries.ru/suppliers-mutual-settlements/reports-implementations/acquiring-reports) по ID отчётов.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1 запрос | 1 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `reportId` | path | integer<int64> | да | ID отчёта |

## Запрос

**Тело запроса** (`application/json`):

- `limit` — integer. Количество строк в ответе По умолчанию: `100000`.
- `rrdId` — integer. ID строки ответа. Необходим для получения отчёта частями. Начинайте загрузку отчёта с `"rrdid":0`. В последующих запросах передавайте значение `rrdId` из последней строки предыдущего ответа. Повторяйте запрос, пока не получите ответ `204` По умолчанию: `0`.
- `fields` — array[string]. Список полей, которые вернутся в ответе. Если параметр не указан, возвращаются все поля

## Ответы

**200** — Успешно

- `rrdId` — integer **обязательный**. ID строки
- `reportId` — integer<int64> **обязательный**. ID отчёта
- `acqDate` — string **обязательный**. Дата операции
- `acquiringBank` — string **обязательный**. Наименование банка-эквайера
- `tin` — string **обязательный**. ИНН
- `taxRegistrationReasonCode` — string **обязательный**. КПП
- `saleDate` — string **обязательный**. Дата продажи
- `srid` — string **обязательный**. ID заказа. В ответах методов сборочных заданий [FBS](./orders-fbs#tag/Sborochnye-zadaniya-FBS), [DBW](./orders-dbw#tag/dbwAssemblyOrders), [DBS](./orders-dbs#tag/dbsAssemblyOrders) и [Самовывоз](./in-store-pickup#tag/inStorePickupAssemblyOrders) `srid` равен `rid`
- `docTypeName` — string **обязательный**. Тип документа
- `nmId` — integer **обязательный**. Артикул WB
- `retailAmount` — string **обязательный**. Вайлдберриз реализовал Товар (Пр)
- `acquiringFee` — string **обязательный**. Размер комиссии за эквайринг, в том числе НДС
- `acquiringFeeVat` — string **обязательный**. Сумма НДС
- `invoiceNumber` — string **обязательный**. Номер счёта-фактуры
- `invoiceDate` — string **обязательный**. Дата счёта-фактуры
- `shkId` — integer **обязательный**. Штрихкод
- `currency` — string **обязательный**. Валюта отчёта

**204** — Нет данных

**400** — Неправильный запрос

- `status` — integer. HTTP статус-код
- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB

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
