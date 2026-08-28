---
title: Создать грузоместо
api: ozon-seller
method: POST
path: /v1/carriage/container/create
operation_id: CarriageContainerCreate
tags:
  - CarriageAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9a548579051f3862
---

# Создать грузоместо

`POST /v1/carriage/container/create`

Вы можете оставить обратную связь по этому методу в комментариях к обсуждению в [сообществе разработчиков Ozon for dev](https://dev.ozon.ru/community/2059-Beta-metody-dlia-raboty-s-doveritelnoi-priemkoi/).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cargo_type` — string **обязательный**. Тип грузоместа: - `box` — коробка; - `pallet` — палета.
- `containers_count` — integer<int32> **обязательный**. Количество грузомест.
- `sort_type` — string **обязательный**. Тип сортировки: - `sort` — сортируемый; - `non-sort` — несортируемый.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Грузоместо создано

- `container_ids` — array[string<int64>]. Идентификаторы грузомест.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
