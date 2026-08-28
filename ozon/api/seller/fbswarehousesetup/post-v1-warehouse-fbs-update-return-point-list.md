---
title: Получить список пунктов возврата для обновления склада
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/update/return-point/list
operation_id: WarehouseFBSUpdateReturnPointList
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 3541ef8d830dc8cc
---

# Получить список пунктов возврата для обновления склада

`POST /v1/warehouse/fbs/update/return-point/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `current_dropoff_point_id` — integer<int64>. Идентификатор выбранной точки отгрузки на складе.
- `current_return_point_id` — integer<int64>. Установленный пункт возврата. Получите значение параметра методом [/v1/warehouse/fbs/return-mile/info](#operation/WarehouseFBSReturnMileInfo).
- `last_id` — integer<int64>. Идентификатор последнего значения на странице.
- `limit` — integer<int32> **обязательный**. Количество значений в ответе.
- `search` — object. Параметры поиска.
  - `address` — string. Адрес пункта возврата.
  - `types` — array[string (PVZ, PPZ, SC)]. Тип пункта возврата: - `PVZ` — пункт выдачи заказов; - `PPZ` — пункт приёма заказов; - `SC` — сортировочный центр.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Успешно

- `has_next` — boolean. Признак, что в ответе вернули не все пункты возврата.
- `is_selected_point_available` — boolean. Признак доступности пункта возврата для выбора.
- `last_id` — integer<int64>. Идентификатор последнего значения на странице.
- `points` — array[object]. Список пунктов возврата.
  - `address` — string. Адрес пункта возврата.
  - `coordinates` — object. Координаты пункта возврата.
    - `latitude` — number<double>. Широта.
    - `longitude` — number<double>. Долгота.
  - `id` — integer<int64>. Идентификатор пункта возврата.
  - `name` — string. Название пункта возврата.
  - `type` — string (UNSPECIFIED, PVZ, PPZ, SC). Тип пункта возврата: - `UNSPECIFIED` — не определён; - `PVZ` — пункт выдачи заказов; - `PPZ` — пункт приёма заказов; - `SC` — сортировочный центр. По умолчанию: `UNSPECIFIED`.
  - `utc_offset` — integer<int32>. Смещение часового пояса от UTC-0 в минутах.
  - `working_days` — array[object]. Рабочие дни пункта.
    - `day` — string (UNSPECIFIED, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY). Дни недели: - `UNSPECIFIED` — не определён, - `MONDAY` — понедельник, - `TUESDAY` — вторник, - `WEDNESDAY` — среда, - `THURSDAY` — четверг, - `FRIDAY` — пятница, - `SATURDAY` — суббота, - `SUNDAY` — воскресенье. По умолчанию: `UNSPECIFIED`.
    - `from` — string. Время начала.
    - `to` — string. Время окончания.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
