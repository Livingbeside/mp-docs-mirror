---
title: Получить список провинций
api: ozon-seller
method: POST
path: /v1/fbp/draft/drop-off/province/list
operation_id: FbpDraftDropOffProvinceList
tags:
  - DraftDropOffFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b443b391bdb59bec
---

# Получить список провинций

`POST /v1/fbp/draft/drop-off/province/list`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Список провинций

- `provinces` — array[object]. Список провинций.
  - `name` — string. Название провинции.
  - `points_count` — integer<int32>. Количество пунктов на карте.
  - `province_uuid` — string. Уникальный идентификатор провинции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
