---
title: Получить статус грузомест FBS
api: ozon-seller
method: POST
path: /v1/carriage/container/status/get
operation_id: CarriageContainerStatusGet
tags:
  - CarriageAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ef98d5564b7e0a1e
---

# Получить статус грузомест FBS

`POST /v1/carriage/container/status/get`

Вы можете оставить обратную связь по этому методу в комментариях к обсуждению в [сообществе разработчиков Ozon for dev](https://dev.ozon.ru/community/2059-Beta-metody-dlia-raboty-s-doveritelnoi-priemkoi/).

## Запрос

**Тело запроса** (`application/json`):

- `container_ids` — array[string<int64>] **обязательный**. Идентификаторы грузомест.

## Ответы

**200** — Статус грузомест

- `containers` — array[object]. Список грузомест.
  - `container_id` — integer<int64>. Идентификатор грузоместа.
  - `status` — string. Статус грузоместа.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
