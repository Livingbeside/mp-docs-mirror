---
title: Получить статус задачи грузового места
api: ozon-seller
method: POST
path: /v1/carriage/container/task/info
operation_id: CarriageContainerTaskInfo
tags:
  - CarriageAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: afafdd8a798fadf7
---

# Получить статус задачи грузового места

`POST /v1/carriage/container/task/info`

Вы можете оставить обратную связь по этому методу в комментариях к обсуждению в [сообществе разработчиков Ozon for dev](https://dev.ozon.ru/community/2059-Beta-metody-dlia-raboty-s-doveritelnoi-priemkoi/).

## Запрос

**Тело запроса** (`application/json`):

- `task_id` — integer<int64>. Идентификатор задачи. Получите его в ответе метода /v1/carriage/container/fill или /v1/carriage/container/approve .

## Ответы

**200** — Статус задачи

- `error_message` — string. Текст ошибки.
- `status` — string. Статус выполнения задачи: - `pending` — в ожидании; - `in_progress` — в процессе; - `completed` — выполнено; - `failed` — ошибка при выполнении;

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
