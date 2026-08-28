---
title: Создать отчёт
api: wb-reports
method: GET
path: /api/v1/warehouse_remains
operation_id: getV1WarehouseRemains
tags:
  - warehousesInventoryReport
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: a7e1945064233a0c
---

# Создать отчёт

`GET /api/v1/warehouse_remains`

Описание метода

Метод создаёт [задание на генерацию](./reports#tag/warehousesInventoryReport/operation/getV1WarehouseRemainsTasksTaskIdStatus) отчёта об [остатках на складах WB](./reports#tag/warehousesInventoryReport/operation/getV1WarehouseRemainsTasksTaskIdDownload).

Параметры `groupBy` и `filter` (группировки и фильтры) можно задать в любой комбинации — аналогично [версии](https://seller.wildberries.ru/analytics-reports/warehouse-remains) в личном кабинете.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 1 запрос | 1 мин | 5 запросов |
| Сервисный | 1 мин | 1 запрос | 1 мин | 5 запросов |
| Базовый с секретом | 1 мин | 1 запрос | 1 мин | 5 запросов |
| Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `locale` | query | string | нет | Язык полей ответа `subjectName` и `warehouseName`: - `ru` — русский - `en` — английский - `zh` — китайский. Значения `warehouseName` на английском |
| `groupByBrand` | query | boolean | нет | Разбивка по брендам |
| `groupBySubject` | query | boolean | нет | Разбивка по предметам |
| `groupBySa` | query | boolean | нет | Разбивка по артикулам продавца |
| `groupByNm` | query | boolean | нет | Разбивка по артикулам WB. Если `groupByNm=true`, в ответе будет поле `volume` |
| `groupByBarcode` | query | boolean | нет | Разбивка по баркодам |
| `groupBySize` | query | boolean | нет | Разбивка по размерам |
| `filterPics` | query | integer | нет | Фильтр по фото: - `-1` — без фото - `0` — не применять фильтр - `1` — с фото |
| `filterVolume` | query | integer | нет | Фильтр по объёму: - `-1` — без габаритов - `0` — не применять фильтр - `3` — свыше трёх литров |

## Ответы

**200** — Успешно

- `data` — object
  - `taskId` — string. ID задания на генерацию

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
