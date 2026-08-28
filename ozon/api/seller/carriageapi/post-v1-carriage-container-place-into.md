---
title: Разместить коробки на палете
api: ozon-seller
method: POST
path: /v1/carriage/container/place-into
operation_id: CarriageContainerPlaceInto
tags:
  - CarriageAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b5db28087ffac0a3
---

# Разместить коробки на палете

`POST /v1/carriage/container/place-into`

Вы можете оставить обратную связь по этому методу в комментариях к обсуждению в [сообществе разработчиков Ozon for dev](https://dev.ozon.ru/community/2059-Beta-metody-dlia-raboty-s-doveritelnoi-priemkoi/).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `child_container_ids` — array[string<int64>] **обязательный**. Идентификаторы грузомест.
- `parent_container_id` — integer<int64> **обязательный**. Идентификатор родительского грузоместа — палеты.

## Ответы

**200** — Задание создано

- `error_containers` — array[object]. Ошибки по грузоместам.
  - `container_id` — integer<int64>. Идентификатор грузоместа.
  - `error_message` — string. Текст ошибки.
- `task_id` — integer<int64>. Идентификатор задания.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
