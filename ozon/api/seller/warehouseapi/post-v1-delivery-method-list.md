---
title: Список методов доставки склада
api: ozon-seller
method: POST
path: /v1/delivery-method/list
operation_id: WarehouseAPI_DeliveryMethodList
tags:
  - WarehouseAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: cdf3109bd87b7261
---

# Список методов доставки склада

`POST /v1/delivery-method/list`

Метод устаревает и будет отключён 7 апреля 2026 года. Переключитесь на /v2/delivery-method/list .

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object. Фильтр для поиска методов доставки.
  - `provider_id` — integer<int64>. Идентификатор службы доставки.
  - `status` — string. Статус метода доставки: - `NEW` — создан, - `EDITED` — редактируется, - `ACTIVE` — активный, - `DISABLED` — неактивный.
  - `warehouse_id` — integer<int64>. Идентификатор склада. Можно получить с помощью метода [/v1/warehouse/list ](#operation/WarehouseAPI_WarehouseList).
- `limit` — integer<int64> **обязательный**. Количество элементов в ответе. Максимум — 50, минимум — 1.
- `offset` — integer<int64>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, то ответ начнётся с 11-го найденного элемента.

## Ответы

**200** — Список методов склада

- `has_next` — boolean. Признак, что в запросе вернулась только часть методов доставки: - `true` — сделайте повторный запрос с новым параметром `offset` для получения остальных методов; - `false` — ответ содержит все методы доставки по запросу.
- `result` — array[object]. Результат запроса.
  - `company_id` — integer<int64>. Идентификатор продавца.
  - `created_at` — string<date-time>. Дата и время создания метода доставки.
  - `cutoff` — string. Время, до которого продавцу нужно собрать заказ.
  - `id` — integer<int64>. Идентификатор метода доставки.
  - `name` — string. Название метода доставки.
  - `provider_id` — integer<int64>. Идентификатор службы доставки.
  - `sla_cut_in` — integer<int64>. Минимальное время на сборку заказа в минутах в соответствии с настройками склада.
  - `status` — string. Статус метода доставки: - `NEW` — создан, - `EDITED` — редактируется, - `ACTIVE` — активный, - `DISABLED` — неактивный.
  - `template_id` — integer<int64>. Идентификатор услуги по доставке заказа.
  - `updated_at` — string<date-time>. Дата и время последнего обновления метода метода доставки.
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
