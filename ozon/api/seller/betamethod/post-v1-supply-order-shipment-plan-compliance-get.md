---
title: Получить информацию о выполнении плана отгрузок
api: ozon-seller
method: POST
path: /v1/supply-order/shipment-plan-compliance/get
operation_id: SupplyOrderShipmentPlanComplianceGet
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 3b5dbdc741a5adb9
---

# Получить информацию о выполнении плана отгрузок

`POST /v1/supply-order/shipment-plan-compliance/get`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2383-Novyi-metod-dlia-polucheniia-informatsii-o-sobliudenii-plana-otgruzok/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Информация о выполнении плана отгрузок

- `compliance_rate_percent` — integer<int32>. Процент выполнения плана отгрузок.
- `interval_days` — integer<int32>. Период в днях, за который рассчитывается процент выполнения плана.
- `min_compliance_percent` — integer<int32>. Минимальный процент выполнения плана отгрузок. Если процент выполнения плана ниже этого значения, применим ограничения из параметра `restrictions`.
- `rate_details` — object. Информация об отгруженных товарах.
  - `max_total_quantity_sum` — integer<int64>. Количество товаров, которые продавец добавил в поставки после их создания. Учитываются поставки, отгруженные за период расчёта.
  - `total_quantity_sum` — integer<int64>. Количество товаров в поставках, отгруженных за период расчёта.
- `restrictions` — object. Информация об ограничениях.
  - `is_restriction_active` — boolean. `true`, если ограничение действует.
  - `max_total_quantity_to_supply` — object. Ограничение на количество товаров в поставке.
    - `applicability` — string (DISABLED, ENABLED). Статус ограничения: - `DISABLED` — не применяется; - `ENABLED` — применяется.
    - `limit` — integer<int64>. Количество единиц товара, которое доступно для отгрузки в кластеры.
  - `timeslot_change` — object. Ограничение на перенос таймслотов.
    - `applicability` — string (DISABLED, ENABLED). Статус ограничения: - `DISABLED` — не применяется; - `ENABLED` — применяется.
    - `change_limit` — integer<int32>. Количество изменений таймслота, которое доступно для поставки.

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
