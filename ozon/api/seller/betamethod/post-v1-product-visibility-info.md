---
title: Получить информацию о видимости товара
api: ozon-seller
method: POST
path: /v1/product/visibility/info
operation_id: ProductVisibilityInfo
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 372cf928dbab3bc0
---

# Получить информацию о видимости товара

`POST /v1/product/visibility/info`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1951-Novyi-metod-upravleniia-vidimostiu-na-vitrinakh/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `skus` — array[string<int64>]. Идентификаторы товаров в системе Ozon — SKU.

## Ответы

**200** — Информация о видимости товара

- `items` — array[object]. Список товаров.
  - `showcases_visibility` — string (UNSPECIFIED, OZON, SELECT, OZON_SELECT, NONE). На каких витринах показывается товар: - `UNSPECIFIED` — не определено; - `OZON` — только на Ozon; - `SELECT` — только на Селект; - `OZON_SELECT` — на Селект и Ozon; - `NONE` — товар скрыт везде. По умолчанию: `UNSPECIFIED`.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
