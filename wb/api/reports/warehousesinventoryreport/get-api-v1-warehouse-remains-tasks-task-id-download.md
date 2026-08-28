---
title: Получить отчёт{{ /api/v1/warehouse_remains/tasks/{task_id}/download }}
api: wb-reports
method: GET
path: /api/v1/warehouse_remains/tasks/{task_id}/download
operation_id: getV1WarehouseRemainsTasksTaskIdDownload
tags:
  - warehousesInventoryReport
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 1ba86b9bc5c4e062
---

# Получить отчёт{{ /api/v1/warehouse_remains/tasks/{task_id}/download }}

`GET /api/v1/warehouse_remains/tasks/{task_id}/download`

Описание метода Метод возвращает отчёт об [остатках на складах WB](https://seller.wildberries.ru/analytics-reports/warehouse-remains) по ID [задания на генерацию](./reports#tag/warehousesInventoryReport/operation/getV1WarehouseRemains). Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 1 запрос | 1 мин | 1 запрос | | Сервисный | 1 мин | 1 запрос | 1 мин | 1 запрос | | Базовый с секретом | 1 мин | 1 запрос | 1 мин | 1 запрос | | Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `task_id` | path | string | да | ID задания на генерацию |

## Ответы

**200** — Успешно

- `brand` — string. Бренд
- `subjectName` — string. Название предмета
- `vendorCode` — string. Артикул продавца
- `nmId` — integer. Артикул WB
- `barcode` — string. Баркод
- `techSize` — string. Размер
- `volume` — number. Объём, л
- `warehouses` — array[object]. Остатки на складах и товары в пути. Будут в ответе только при ненулевом `quantity`
  - `warehouseName` — string. Название склада
  - `quantity` — integer. Количество, шт.

**204** — Нет данных

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

**404** — Не найдено

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
