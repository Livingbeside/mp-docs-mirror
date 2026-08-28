---
title: Обновить метод доставки «Вы или сторонняя служба»
api: ozon-seller
method: POST
path: /v1/warehouse/erfbs/non-integrated/delivery-method/update
operation_id: WarehouseERFBSNonIntegratedDeliveryMethodUpdate
tags:
  - rFBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9b6cb746891c24c9
---

# Обновить метод доставки «Вы или сторонняя служба»

`POST /v1/warehouse/erfbs/non-integrated/delivery-method/update`

[Подробнее о схеме rFBS Express](https://seller-edu.ozon.ru/rfbs/scheme-of-work/rfbs-express#%D1%87%D1%82%D0%BE-%D1%82%D0%B0%D0%BA%D0%BE%D0%B5-realfbs-express)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `courier_cutoff` — integer (5, 10, 15, 20, 25, 30, 35, 40, 45) **обязательный**. Скорость отгрузки.
- `cut_in` — integer (15, 30, 60, 120, 180, 240, 300, 360, 420, 480) **обязательный**. Время сборки.
- `delivery_method_id` — integer<int64> **обязательный**. Идентификатор метода доставки.
- `name` — string **обязательный**. Название метода доставки.
- `return_settings` — object **обязательный**. Настройки возвратов от покупателей.
  - `contact_days` — integer<int64>. Количество дней, за которое вы свяжетесь с покупателем. Параметр обязательный, если `return_method = COURIER`.
  - `post_office_zipcode` — string. Индекс отделения Почты России.
  - `return_method` — string (COURIER, TRANSPORT_COMPANY) **обязательный**. Способ возврата: - `COURIER` — курьером; - `TRANSPORT_COMPANY` — транспортной компанией.
  - `transport_company_name` — string. Название транспортной компании. Параметр обязательный, если `return_method = TRANSPORT_COMPANY`.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Успешно

- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
