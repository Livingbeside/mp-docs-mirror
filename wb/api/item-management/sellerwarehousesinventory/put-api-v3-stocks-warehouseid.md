---
title: Обновить остатки товаров{{ /api/v3/stocks/{warehouseId} }}
api: wb-item-management
method: PUT
path: /api/v3/stocks/{warehouseId}
operation_id: putV3StocksWarehouseId
tags:
  - sellerWarehousesInventory
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: e8ccff5dff86be58
---

# Обновить остатки товаров{{ /api/v3/stocks/{warehouseId} }}

`PUT /api/v3/stocks/{warehouseId}`

Описание метода

Метод обновляет количество остатков товаров продавца [в списке](./item-management#tag/sellerWarehousesInventory/operation/postV3StocksWarehouseId).

 Названия параметров запроса не валидируются. При отправке некорректных названий вы получите успешный ответ (204), но остатки не обновятся.

Лимит запросов на один аккаунт продавца для всех методов остатков на складах продавца кроме метода удаления остатков:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `warehouseId` | path | integer<int64> | да | ID склада продавца |

## Запрос

**Тело запроса** (`application/json`):

- `stocks` — array[object] **обязательный**. Массив ID размеров товаров и их остатков
  - `chrtId` — integer. ID размера товара
  - `amount` — integer. Остаток

## Ответы

**204** — Обновлено

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

**406** — Обновление остатков заблокировано

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**409** — Ошибка обновления остатков

- `data` — array[object]. Дополнительная информация об ошибке
  - `sku` — string. Баркод
  - `chrtId` — integer. ID размера товара
  - `amount` — integer. Остаток
- `code` — string. Код ошибки
- `message` — string. Описание ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
