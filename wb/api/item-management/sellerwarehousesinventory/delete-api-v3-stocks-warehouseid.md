---
title: Удалить остатки товаров{{ /api/v3/stocks/{warehouseId} }}
api: wb-item-management
method: DELETE
path: /api/v3/stocks/{warehouseId}
operation_id: deleteV3StocksWarehouseId
tags:
  - sellerWarehousesInventory
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: fb6bea3768796f50
---

# Удалить остатки товаров{{ /api/v3/stocks/{warehouseId} }}

`DELETE /api/v3/stocks/{warehouseId}`

Описание метода

Метод удаляет запись об остатках товаров продавца из [списка остатков](./item-management#tag/sellerWarehousesInventory/operation/postV3StocksWarehouseId).

 Действие необратимо. Удаленный остаток будет необходимо загрузить повторно для возобновления продаж.

Лимит запросов на один профиль продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 10 запросов | 6 сек | 2 запроса |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `warehouseId` | path | integer<int64> | да | ID склада продавца |

## Запрос

**Тело запроса** (`application/json`):

- `chrtIds` — array[integer<uint64>] **обязательный**. Массив ID размеров товаров

## Ответы

**204** — Удалено

**400** — Неправильный запрос

- `code` — string **обязательный**. Код ошибки
- `message` — string **обязательный**. Детали ошибки

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

**409** — Конфликт

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
