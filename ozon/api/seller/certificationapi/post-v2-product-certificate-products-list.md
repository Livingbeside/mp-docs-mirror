---
title: Получить список товаров, которые привязаны к сертификату
api: ozon-seller
method: POST
path: /v2/product/certificate/products/list
operation_id: ProductCertificateProductsListV2
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 63b4958ba25d198a
---

# Получить список товаров, которые привязаны к сертификату

`POST /v2/product/certificate/products/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `certificate_id` — integer<int32> **обязательный**. Идентификатор сертификата. Получите методом [/v1/product/certificate/list](#operation/CertificateList).
- `filter` — object. Фильтр.
  - `status` — string. Статус проверки товара при привязке к сертификату: - `awaiting_verification` — ожидает проверки; - `approved` — проверка пройдена; - `declined` — проверка не пройдена; - `background_check` — на проверке.
- `last_id` — integer<int64>. Идентификатор последнего значения на странице. При первом запросе оставьте это поле пустым. Чтобы получить следующие значения, укажите последнее значение `products.sku` из ответа предыдущего запроса.
- `limit` — integer<int64> **обязательный**. Количество значений в ответе.

## Ответы

**200** — Список товаров

- `products` — array[object]. Товары, которые привязаны к сертификату.
  - `image` — string. Изображение товара.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `status` — string. Статус проверки товара при привязке к сертификату: - `awaiting_verification` — ожидает проверки; - `approved` — проверка пройдена; - `declined` — проверка не пройдена; - `background_check` — на проверке.
- `total` — integer<int64>. Общее количество товаров, которые привязаны к сертификату.

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
