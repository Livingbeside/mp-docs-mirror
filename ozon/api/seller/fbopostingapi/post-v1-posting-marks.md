---
title: Получить маркировки экземпляров из отправления
api: ozon-seller
method: POST
path: /v1/posting/marks
operation_id: PostingAPI_PostingMarks
tags:
  - FboPostingAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 2a03b24b4867e34f
---

# Получить маркировки экземпляров из отправления

`POST /v1/posting/marks`

Возвращает статусы выдачи экземпляров и коды маркировки «Честный ЗНАК» для каждого отправления.

Укажите в чеке и выведите из оборота маркировки экземпляров из параметра `issued_exemplars` в ответе.

## Запрос

**Тело запроса** (`application/json`):

- `posting_numbers` — array[string]. Идентификаторы отправлений.

## Ответы

**200** — Список экземпляров отправления с маркировками

- `invalid_postings` — array[string]. Список неверных идентификаторов отправлений.
- `issued_exemplars` — array[object]. Список выданных покупателям экземпляров товаров.
  - `exemplar_id` — integer<int64>. Идентификатор экземпляра.
  - `mandatory_marks` — array[string]. Cписок маркировок выданных покупателям экземпляров.
  - `posting_number` — string. Идентификатор отправления.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
- `non_issued_exemplars` — array[object]. Список не выданных покупателям экземпляров товаров.
  - `exemplar_id` — integer<int64>. Идентификатор экземпляра.
  - `posting_number` — string. Идентификатор отправления.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
