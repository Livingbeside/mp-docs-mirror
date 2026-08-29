---
title: Информация о заявке на возврат
api: ozon-seller
method: POST
path: /v2/returns/rfbs/get
operation_id: RFBSReturnsAPI_ReturnsRfbsGetV2
tags:
  - RFBSReturnsAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 1cac95a43a1aec95
---

# Информация о заявке на возврат

`POST /v2/returns/rfbs/get`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `return_id` — integer<int64> **обязательный**. Идентификатор заявки на возврат. Получите методом [/v2/returns/rfbs/list](#operation/RFBSReturnsAPI_ReturnsRfbsListV2).

## Ответы

**200** — Информация о заявке

- `returns` — object. Данные о заявке.
  - `available_actions` — array[object]. Данные о доступных действиях с заявкой.
    - `id` — integer<int32>. Идентификатор действия.
    - `name` — string. Название действия.
  - `client_name` — string. Имя покупателя.
  - `client_photo` — array[string]. Ссылки на фотографии товара.
  - `client_return_method_type` — object. Данные о способе возврата.
    - `id` — integer<int32>. Идентификатор.
    - `name` — string. Название.
  - `comment` — string. Комментарий покупателя.
  - `created_at` — string<date-time>. Дата создания заявки.
  - `order_number` — string. Номер заказа.
  - `posting_number` — string. Номер отправления.
  - `product` — object. Данные о товаре.
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `currency_code` — string. Валюта ваших цен. Cовпадает с валютой, которая установлена в настройках личного кабинета. Возможные значения: - `RUB` — российский рубль, - `BYN` — белорусский рубль, - `KZT` — тенге, - `EUR` — евро, - `USD` — доллар США, - `CNY` — юань.
    - `price` — integer<int32>. Цена товара.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `rejection_comment` — string. Комментарий об отклонении заявки.
  - `rejection_reason` — array[object]. Данные о причине отклонения заявки.
    - `hint` — string. Подсказка о дальнейших действиях с возвратом.
    - `id` — integer<int32>. Идентификатор причины.
    - `is_comment_required` — boolean. Признак, нужно ли прикладывать комментарий.
    - `name` — string. Описание причины.
  - `return_method_description` — string. Способ возврата товара.
  - `return_number` — string. Номер заявки на возврат.
  - `return_reason` — object. Данные о причине возврата.
    - `id` — integer<int32>. Идентификатор причины.
    - `is_defect` — boolean. Признак, является ли товар бракованным.
    - `name` — string. Описание причины.
  - `ru_post_tracking_number` — string. Трек-номер почтового отправления.
  - `state` — object. Данные о статусе возврата.
    - `state` — string. Статус.
    - `state_name` — string. Название статуса на русском.
  - `warehouse_id` — integer<int64>. Идентификатор склада.

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
