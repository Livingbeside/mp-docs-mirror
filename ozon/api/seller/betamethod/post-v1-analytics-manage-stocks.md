---
title: Управление остатками
api: ozon-seller
method: POST
path: /v1/analytics/manage/stocks
operation_id: AnalyticsAPI_ManageStocks
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ce014d9f53a730c0
---

# Управление остатками

`POST /v1/analytics/manage/stocks`

22 января 2026 года метод будет отключён. Переключитесь на [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks).

Используйте метод, чтобы узнать, сколько товаров осталось на складах FBO.

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1106-Razdel-upravleniia-ostatkami-analytics-manage-stocks)
в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object. Фильтр.
  - `skus` — array[string<int64>]. Идентификаторы товаров в системе Ozon — SKU.
  - `stock_types` — array[string (STOCK_TYPE_VALID, STOCK_TYPE_WAITING_DOCS, STOCK_TYPE_EXPIRING, STOCK_TYPE_DEFECT)]. Тип оставшегося на складе товара: - `STOCK_TYPE_VALID` — валидный сток. Остаток товара, доступного для продажи. - `STOCK_TYPE_WAITING_DOCS` — превалидный сток. Остаток товара, который Ozon не может продавать, пока продавец не прислал в Ozon документы по обязательной маркировке. Товар перейдёт в валидный сток, когда документы будут подписаны. - `STOCK_TYPE_EXPIRING` — предпросрок. Остаток товара, который снят с полки, но срок годности формально не истёк. - `STOCK_TYPE_DEFECT` — брак. Остаток товара, который находится на складах Ozon, но повреждён.
  - `warehouse_ids` — array[string<int64>]. Идентификаторы складов.
- `limit` — integer<int32>. Количество значений в ответе.
- `offset` — integer<int32>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, ответ начнётся с 11-го найденного элемента.

## Ответы

**200** — Информация об остатках

- `items` — array[object]. Товары.
  - `defect_stock_count` — integer<int64>. Остаток дефектного товара, шт.
  - `expiring_stock_count` — integer<int64>. Остаток товара с истекающим сроком годности, шт.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `valid_stock_count` — integer<int64>. Остаток товара, доступного для продажи.
  - `waitingdocs_stock_count` — integer<int64>. Остаток товара, ожидающего документы.
  - `warehouse_name` — string. Название склада.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
