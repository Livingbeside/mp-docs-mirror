---
title: Список эконом-товаров
api: ozon-seller
method: POST
path: /v1/product/quant/list
operation_id: QuantProductList
tags:
  - Quants
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e3270b45841dfabf
---

# Список эконом-товаров

`POST /v1/product/quant/list`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1084-Metody-po-tarifu-Ekonom) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `limit` — integer<int64> **обязательный**. Максимальное количество элементов в ответе.
- `visibility` — string (ALL, VISIBLE, INVISIBLE, EMPTY_STOCK, NOT_MODERATED, MODERATED, DISABLED, STATE_FAILED, READY_TO_SUPPLY, VALIDATION_STATE_PENDING, VALIDATION_STATE_FAIL, VALIDATION_STATE_SUCCESS…). Фильтр по видимости товара: - `ALL` — все товары, кроме архивных. - `VISIBLE` — товары, которые видны покупателям. - `INVISIBLE` — товары, которые не видны покупателям. - `EMPTY_STOCK` — товары, которых нет в наличии. - `NOT_MODERATED` — товары, которые не прошли модерацию. - `MODERATED` — товары, которые прошли модерацию. - `DISABLED` — товары, которые видны покупателям, но недоступны к покупке. - `STATE_FAILED` — товары, создание которых завершилось ошибкой. - `READY_TO_SUPPLY` — товары, готовые к поставке. - `VALIDATION_STATE_PENDING` — товары, которые проходят проверку валидатором на премодерации. - `VALIDATION_STATE_FAIL` — товары, которые не прошли проверку валидатором на премодерации. - `VALIDATION_STATE_SUCCESS` — товары, которые прошли проверку валидатором на премодерации. - `TO_SUPPLY` — товары, готовые к продаже. - `IN_SALE` — товары в продаже. - `REMOVED_FROM_SALE` — товары, скрытые от покупателей. - `OVERPRICED` — превышение цены. - `CRITICALLY_OVERPRICED` — критическое превышение цены. - `EMPTY_BARCODE` — пустой штрихкод. - `BARCODE_EXISTS` — штрихкод указан. - `QUARANTINE` — товар в карантине после изменения цены на 50% и больше. - `ARCHIVED` — товары в архиве. - `OVERPRICED_WITH_STOCK` — товары в продаже, цена которых выше, чем у конкурентов. - `PARTIAL_APPROVED` — товары в продаже, у которых пустое или неполное описание. По умолчанию: `ALL`.

## Ответы

**200** — Эконом-товары

- `cursor` — string. Указатель для выборки следующих данных.
- `products` — ?. Эконом-товары.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `quants` — ?. Список квантов товара.
    - `quant_code` — string. Идентификатор кванта.
    - `quant_size` — integer<int64>. Размер кванта.
- `total_items` — integer<int32>. Остаток на всех складах, шт.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
