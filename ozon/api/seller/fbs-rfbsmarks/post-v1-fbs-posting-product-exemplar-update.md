---
title: Обновить данные экземпляров
api: ozon-seller
method: POST
path: /v1/fbs/posting/product/exemplar/update
operation_id: PostingAPI_FbsPostingProductExemplarUpdate
tags:
  - FBS&rFBSMarks
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: c16124ddeeb671b7
---

# Обновить данные экземпляров

`POST /v1/fbs/posting/product/exemplar/update`

Используйте метод после передачи информации по экземплярам методом [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6), чтобы сохранить обновлённые данные по экземплярам для отправлений в статусе «Ожидает отгрузки».

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления.

## Ответы

**200** — Данные обновлены

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
