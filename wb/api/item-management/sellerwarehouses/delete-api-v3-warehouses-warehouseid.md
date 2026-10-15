---
title: Удалить склад продавца{{ /api/v3/warehouses/{warehouseId} }}
api: wb-item-management
method: DELETE
path: /api/v3/warehouses/{warehouseId}
operation_id: deleteV3WarehousesWarehouseId
tags:
  - sellerWarehouses
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: e127e60cf0b4fabc
---

# Удалить склад продавца{{ /api/v3/warehouses/{warehouseId} }}

`DELETE /api/v3/warehouses/{warehouseId}`

Описание метода

Метод удаляет [склад продавца](./item-management#tag/sellerWarehouses/operation/getV3Warehouses).

Лимит запросов на один профиль продавца для всех методов складов продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `warehouseId` | path | integer<int64> | да | ID склада продавца |

## Ответы

**204** — Удалено

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

- `code` — string **обязательный**. Код ошибки
- `message` — string **обязательный**. Детали ошибки

**404** — Не найдено

- `code` — string **обязательный**. Код ошибки
- `message` — string **обязательный**. Детали ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
