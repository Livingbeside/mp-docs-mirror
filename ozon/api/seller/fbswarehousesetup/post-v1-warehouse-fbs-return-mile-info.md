---
title: Получить информацию о возвратной миле
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/return-mile/info
operation_id: WarehouseFBSReturnMileInfo
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: fd8d77542de69f50
---

# Получить информацию о возвратной миле

`POST /v1/warehouse/fbs/return-mile/info`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `warehouse_ids` — array[string<int64>] **обязательный**. Идентификаторы складов.

## Ответы

**200** — Успешно

- `return_mile_settings` — array[object]. Информация о возвратной миле на складе.
  - `is_return_mile_required` — boolean. Признак, что необходимо установить пункт возврата.
  - `return_point` — object. Информация о пункте возврата.
    - `address` — string. Адрес пункта возврата.
    - `coordinates` — object. Координаты пункта возврата.
      - `latitude` — number<double>. Широта.
      - `longitude` — number<double>. Долгота.
    - `id` — integer<int64>. Идентификатор пункта возврата.
    - `name` — string. Название пункта возврата.
    - `type` — string (UNSPECIFIED, PVZ, PPZ, SC). Тип пункта возврата: - `UNSPECIFIED` — не определён; - `PVZ` — пункт выдачи заказов; - `PPZ` — пункт приёма заказов; - `SC` — сортировочный центр. По умолчанию: `UNSPECIFIED`.
    - `utc_offset` — integer<int32>. Смещение часового пояса от UTC-0 в минутах.
    - `working_days` — array[object]. Рабочие дни пункта возврата.
      - `day` — string (UNSPECIFIED, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY). Дни недели: - `UNSPECIFIED` — не определён, - `MONDAY` — понедельник, - `TUESDAY` — вторник, - `WEDNESDAY` — среда, - `THURSDAY` — четверг, - `FRIDAY` — пятница, - `SATURDAY` — суббота, - `SUNDAY` — воскресенье. По умолчанию: `UNSPECIFIED`.
      - `from` — string. Время начала.
      - `to` — string. Время окончания.
  - `warehouse_id` — integer<int64>. Идентификатор склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
