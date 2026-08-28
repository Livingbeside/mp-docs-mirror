---
title: Подтвердить состав грузоместа
api: ozon-seller
method: POST
path: /v1/carriage/container/approve
operation_id: CarriageContainerApprove
tags:
  - CarriageAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: c8bfc3ea9ece0ef7
---

# Подтвердить состав грузоместа

`POST /v1/carriage/container/approve`

Вы можете оставить обратную связь по этому методу в комментариях к обсуждению в [сообществе разработчиков Ozon for dev](https://dev.ozon.ru/community/2059-Beta-metody-dlia-raboty-s-doveritelnoi-priemkoi/).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `container_ids` — array[string<int64>] **обязательный**. Идентификаторы грузомест.

## Ответы

**200** — Состав подтверждён

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
