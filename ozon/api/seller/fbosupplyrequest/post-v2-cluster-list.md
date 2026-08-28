---
title: Получить информацию о макролокальных кластерах
api: ozon-seller
method: POST
path: /v2/cluster/list
operation_id: DraftClusterList
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 07ef01031d26e694
---

# Получить информацию о макролокальных кластерах

`POST /v2/cluster/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Макролокальные кластеры

- `result` — array[object]. Список кластеров.
  - `data` — object. Кластер.
    - `fulfillments` — array[object]. Склады Ozon в кластере.
      - `name` — string. Название склада.
      - `warehouse_id` — integer<int64>. Идентификатор склада.
    - `macrolocal_cluster` — object. Информация о кластере.
      - `country` — object. Информация о стране кластера.
        - `name` — string. Название страны.
        - `uid` — string. Идентификатор страны.
      - `name` — string. Название кластера.
  - `macrolocal_cluster_id` — integer<int64>. Идентификатор кластера.

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
