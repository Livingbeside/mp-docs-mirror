---
title: Получить этикетку по грузоместам
api: ozon-seller
method: POST
path: /v1/carriage/container/label/get
operation_id: CarriageContainerLabelGet
tags:
  - CarriageAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 07879ee5331a912c
---

# Получить этикетку по грузоместам

`POST /v1/carriage/container/label/get`

Вы можете оставить обратную связь по этому методу в комментариях к обсуждению в [сообществе разработчиков Ozon for dev](https://dev.ozon.ru/community/2059-Beta-metody-dlia-raboty-s-doveritelnoi-priemkoi/).

## Запрос

**Тело запроса** (`application/json`):

- `container_ids` — array[string<int64>]. Идентификаторы грузомест.

## Ответы

**200** — Список этикеток

- `content` — object. Информация о сформированной этикетке.
  - `content_type` — string. Тип файла.
  - `file_content` — string<byte>. Содержание файла в бинарном виде.
  - `file_name` — string. Название файла.
- `error_containers` — array[object]. Ошибки грузомест, по которым не удалось сформировать этикетку.
  - `container_id` — integer<int64>. Идентификатор грузоместа.
  - `error_message` — string. Текст ошибки.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
