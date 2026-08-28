---
title: Получить документы по грузоместам — ТрН и лист отгрузки
api: ozon-seller
method: POST
path: /v1/carriage/container/document/get
operation_id: CarriageContainerDocumentGet
tags:
  - CarriageAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f4e28713e11db61d
---

# Получить документы по грузоместам — ТрН и лист отгрузки

`POST /v1/carriage/container/document/get`

Вы можете оставить обратную связь по этому методу в комментариях к обсуждению в [сообществе разработчиков Ozon for dev](https://dev.ozon.ru/community/2059-Beta-metody-dlia-raboty-s-doveritelnoi-priemkoi/).

## Запрос

**Тело запроса** (`application/json`):

- `container_ids` — array[string<int64>] **обязательный**. Идентификаторы грузомест.

## Ответы

**200** — Список документов

- `content_type` — string. Тип файла: application или pdf.
- `file_content` — string<byte>. Содержание файла в бинарном виде.
- `file_name` — string. Название файла.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
