---
title: Количество возвратов FBS
api: ozon-seller
method: POST
path: /v1/returns/company/fbs/info
operation_id: returnsCompanyFBSInfo
tags:
  - ReturnAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a3877925ece7f34c
---

# Количество возвратов FBS

`POST /v1/returns/company/fbs/info`

Метод для получения информации о возвратах FBS и их количестве.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object. Фильтры.
  - `place_id` — integer<int64>. Фильтр по идентификатору drop-off пункта.
- `pagination` — object **обязательный**. Разделение ответа метода.
  - `last_id` — integer<int64>. Идентификатор последнего drop-off пункта на странице. Для первого запроса оставьте это поле пустым. Чтобы получить следующие значения, укажите `id` последнего drop-off пункта из ответа предыдущего запроса.
  - `limit` — integer<int32> **обязательный**. Количество drop-off пунктов на странице. Максимум — 500.

## Ответы

**200** — Количество возвратов FBS

- `drop_off_points` — array[object]. Информация о drop-off пунктах.
  - `address` — string. Адрес drop-off пункта.
  - `box_count` — integer<int32>. Количество коробок в drop-off пункте.
  - `id` — integer<int64>. Идентификатор drop-off пункта.
  - `name` — string. Название drop-off пункта.
  - `pass_info` — object. Информация о пропуске.
    - `count` — integer<int32>. Количество пропусков на drop-off пункт.
    - `is_required` — boolean. Признак, нужен ли пропуск на drop-off пункт.
  - `place_id` — integer<int64>. Идентификатор склада, на который приедет отгрузка.
  - `returns_count` — integer<int32>. Количество возвратов в drop-off пункте.
  - `utc_offset` — string. Смещение часового пояса времени отгрузки от UTC-0.
  - `warehouses_ids` — array[string<int64>]. Идентификатор складов продавца.
- `has_next` — boolean. Признак, есть ли ещё пункты, где продавца ожидают возвраты.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
