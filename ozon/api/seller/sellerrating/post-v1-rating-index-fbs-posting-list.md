---
title: Список отправлений, которые повлияли на индекс ошибок FBS и rFBS
api: ozon-seller
method: POST
path: /v1/rating/index/fbs/posting/list
operation_id: RatingAPI_ListFBSRatingIndexPostingsV1
tags:
  - SellerRating
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 8a2070d47f7b9a2c
---

# Список отправлений, которые повлияли на индекс ошибок FBS и rFBS

`POST /v1/rating/index/fbs/posting/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object **обязательный**. Фильтр.
  - `date_from` — string<date-time> **обязательный**. Дата начала периода.
  - `date_to` — string<date-time> **обязательный**. Дата конца периода.
  - `posting_numbers` — array[string]. Номера отправлений.
- `limit` — integer<int64> **обязательный**. Количество значений в ответе.

## Ответы

**200** — Список отправлений

- `cursor` — string. Указатель для выборки следующих данных.
- `errors` — array[object]. Отправления, которые повлияли на индекс.
  - `charge_percent` — number<double>. Процент стоимости обработки от стоимости отправления.
  - `charge_price` — number<double>. Стоимость обработки ошибок.
  - `charge_price_currency_code` — string. Код валюты стоимости обработки ошибок: - `RUB` — российский рубль, - `BYN` — белорусский рубль, - `KZT` — тенге, - `EUR` — евро, - `USD` — доллар США, - `CNY` — юань.
  - `delivery_schema` — string. Схема доставки: - `FBS`, - `rFBS`, - `erFBS`.
  - `error_at` — string<date-time>. Дата, когда возникла ошибка.
  - `has_grace_status` — boolean. `true`, если у отправления льготный статус.
  - `index` — number<double>. Значение индекса ошибок.
  - `posting_error_type` — string (UNSPECIFIED, SELLER_CANCELLATION, SELLER_DELAY). Тип ошибки: - `UNSPECIFIED` — не указан; - `SELLER_CANCELLATION` — отмена по вине продавца; - `SELLER_DELAY` — просрочка по вине продавца. По умолчанию: `UNSPECIFIED`.
  - `posting_number` — string. Номер отправления.
  - `product_price` — number<double>. Стоимость товара в отправлении.
  - `product_price_currency_code` — string. Код валюты стоимости товара: - `RUB` — российский рубль, - `BYN` — белорусский рубль, - `KZT` — тенге, - `EUR` — евро, - `USD` — доллар США, - `CNY` — юань.
- `has_next` — boolean. `true`, если в ответе вернулись не все отправления.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
