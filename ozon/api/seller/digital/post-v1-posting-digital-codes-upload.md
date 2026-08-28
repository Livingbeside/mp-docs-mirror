---
title: Загрузить коды цифровых товаров для отправления
api: ozon-seller
method: POST
path: /v1/posting/digital/codes/upload
operation_id: UploadPostingCodes
tags:
  - Digital
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a87bb20d2842c8a2
---

# Загрузить коды цифровых товаров для отправления

`POST /v1/posting/digital/codes/upload`

Метод доступен только продавцам, работающим с цифровыми товарами. Вы можете загрузить коды цифровых товаров в течение 24 часов с момента получения заказа.

Передайте все коды цифровых товаров к каждому товару в заказе за один запрос. Если передадите не все коды, запрос вернётся с ошибкой.

## Запрос

**Тело запроса** (`application/json`):

- `exemplars_by_sku` — array[object]. Данные о кодах цифрового товара по SKU.
  - `exemplar_keys` — array[string]. Список кодов цифрового товара. Количество кодов должно совпадать со значением параметра `exemplar_qty`.
  - `exemplar_qty` — integer<int32> **обязательный**. Количество кодов цифрового товара, которые вы передаёте покупателю. Сумма значений в параметрах `exemplar_qty ` и `not_available_exemplar_qty` должна равняться количеству кодов в заказе. Получите это значение в параметре `required_qty_for_digital_code` в ответе метода [/v1/posting/digital/list](#operation/ListPostingCodes).
  - `not_available_exemplar_qty` — integer<int32> **обязательный**. Количество кодов цифрового товара, которые вы не можете передать покупателю. Сумма значений в параметрах `exemplar_qty ` и `not_available_exemplar_qty` должна равняться количеству кодов в заказе. Получите это значение в параметре `required_qty_for_digital_code` в ответе метода [/v1/posting/digital/list](#operation/ListPostingCodes).
  - `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.
- `posting_number` — string. Номер отправления.

## Ответы

**200** — Коды цифровых товаров загружены

- `exemplars_by_sku` — array[object]. Данные о кодах цифрового товара по SKU.
  - `failed_exemplars` — array[object]. Список кодов цифровых товаров с ошибками.
    - `key` — string. Значение кода цифрового товара.
    - `message` — string. Текст ошибки.
  - `received_qty` — integer<int32>. Количество кодов цифрового товара, которые были приняты.
  - `rejected_qty` — integer<int32>. Количество кодов цифровых товаров, которые не были приняты или переданы.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
