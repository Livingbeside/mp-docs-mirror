---
title: Получить историю отгрузок курьерам
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/pickup/history/list
operation_id: WarehouseFbsPickUpHistoryList
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e55a149f2b5dc78b
---

# Получить историю отгрузок курьерам

`POST /v1/warehouse/fbs/pickup/history/list`

[Подробнее об отгрузках курьеру в Базе знаний продавца](https://seller-edu.ozon.ru/fbs/ozon-logistika/otgruzka-kyruery)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object. Фильтр.
  - `planned_date` — string. Дата отгрузки.
  - `warehouse_id` — array[string<int64>]. Идентификаторы складов.
  - `was_planned` — boolean. `true`, если отгрузка запланирована.
- `limit` — integer<int64> **обязательный**. Количество значений на странице.

## Ответы

**200** — История отгрузок

- `result` — object. Результат метода.
  - `cursor` — string. Указатель для выборки следующих данных.
  - `history` — array[object]. История отгрузок.
    - `planned_date` — string. Дата отгрузки в формате `YYYY-MM-DD`.
    - `status` — string. Статус отгрузки: - `courier_called` — продавец вызвал курьера самостоятельно; - `courier_cancelled` — продавец отменил курьера; - `courier_assigned` — Ozon назначил курьера автоматически; - `courier_not_assigned` — курьер не назначен.
    - `updated_at` — string<date-time>. Дата и время обновления отгрузки.
    - `warehouse_id` — integer<int64>. Идентификатор склада.
    - `warehouse_name` — string. Название склада.
    - `was_planned` — boolean. `true`, если отгрузка запланирована.

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
