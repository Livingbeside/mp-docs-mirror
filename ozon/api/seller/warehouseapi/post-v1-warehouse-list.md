---
title: Список складов
api: ozon-seller
method: POST
path: /v1/warehouse/list
operation_id: WarehouseAPI_WarehouseList
tags:
  - WarehouseAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 78234b4879f23004
---

# Список складов

`POST /v1/warehouse/list`

Метод устаревает и будет отключён 7 апреля 2026 года. Переключитесь на [/v2/warehouse/list](#operation/WarehouseListV2).

Возвращает список складов FBS и rFBS. Чтобы получить список складов FBO, используйте метод [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList).

Метод можно использовать 1 раз в минуту.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `limit` — integer<int64> **обязательный**. Количество значений в ответе.
- `offset` — integer<int64>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, то ответ начнётся с 11-го найденного элемента.
- `with` — object. Дополнительные поля, которые нужно добавить в ответ.
  - `able_to_set_price` — boolean. `true`, чтобы добавить в ответ информацию о возможности установить цену.

## Ответы

**200** — Список складов

- `result` — array[object]. Список складов.
  - `has_entrusted_acceptance` — boolean. Признак доверительной приёмки. `true`, если доверительная приёмка включена на складе.
  - `is_rfbs` — boolean. Признак работы склада по схеме rFBS: - `true` — склад работает по схеме rFBS; - `false` — не работает по схеме rFBS.
  - `name` — string. Название склада.
  - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `can_print_act_in_advance` — boolean. Возможность печати акта приёма-передачи заранее. `true`, если печатать заранее возможно.
  - `first_mile_type` — object. Первая миля FBS.
    - `dropoff_point_id` — string. Идентификатор DropOff-точки.
    - `dropoff_timeslot_id` — integer<int64>. Идентификатор временного слота для DropOff.
    - `first_mile_is_changing` — boolean. Признак, что настройки склада обновляются.
    - `first_mile_type` — string (DropOff, Pickup). Тип первой мили — `DropOff` или `Pickup`.
  - `has_postings_limit` — boolean. Признак наличия лимита минимального количества заказов. `true`, если лимит есть.
  - `is_karantin` — boolean. Признак, что склад не работает из-за карантина.
  - `is_kgt` — boolean. Признак, что склад принимает крупногабаритные товары.
  - `is_economy` — boolean. `true`, если склад работает с эконом-товарами.
  - `is_able_to_set_price` — boolean. `true`, если можно установить цену.
  - `is_presorted` — boolean. `true`, если отгрузка с предсортировкой.
  - `is_timetable_editable` — boolean. Признак, что можно менять расписание работы складов.
  - `min_postings_limit` — integer<int32>. Минимальное значение лимита — количество заказов, которые можно привезти в одной поставке.
  - `postings_limit` — integer<int32>. Значение лимита. `-1`, если лимита нет.
  - `min_working_days` — integer<int64>. Количество рабочих дней склада.
  - `status` — string. Статус склада. Соответствие статусов склада со статусами с личном кабинете: | Статус Seller&nbsp;API | Статус в личном кабинете | |---|---| | `new` | Активируется | | `created` | Активный | | `disabled` | В архиве | | `blocked` | Заблокирован | | `disabled_due_to_limit` | На паузе | | `error` | Ошибка |
  - `working_days` — ?. Рабочие дни склада.

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
