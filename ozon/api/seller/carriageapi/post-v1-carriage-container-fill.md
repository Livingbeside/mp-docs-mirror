---
title: Наполнить грузоместо отправлениями
api: ozon-seller
method: POST
path: /v1/carriage/container/fill
operation_id: CarriageContainerFill
tags:
  - CarriageAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 534f3ca33ca88917
---

# Наполнить грузоместо отправлениями

`POST /v1/carriage/container/fill`

Вы можете оставить обратную связь по этому методу в комментариях к обсуждению в [сообществе разработчиков Ozon for dev](https://dev.ozon.ru/community/2059-Beta-metody-dlia-raboty-s-doveritelnoi-priemkoi/).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `container_id` — integer<int64> **обязательный**. Идентификатор грузоместа.
- `posting_numbers` — array[string] **обязательный**. Номера отправлений.

## Ответы

**200** — Задание создано

- `error_postings` — array[object]. Ошибки по отправлениям.
  - `error_message` — string. Текст ошибки.
  - `posting_number` — string. Номер отправления.
- `task_id` — integer<int64>. Идентификатор задания.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
