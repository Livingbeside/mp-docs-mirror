---
title: Статус формирования накладной
api: ozon-seller
method: POST
path: /v2/posting/fbs/digital/act/check-status
operation_id: PostingAPI_PostingFBSDigitalActCheckStatus
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: eaaa586db0bf1997
---

# Статус формирования накладной

`POST /v2/posting/fbs/digital/act/check-status`

> ⚠️ Метод помечен как **deprecated**.

Метод устаревает и будет отключён 22 марта 2026 года. Переключитесь на /v2/posting/fbs/act/check-status.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `id` — integer<int64> **обязательный**. Номер задания на формирование документов (также идентификатор перевозки) из метода [POST /v2/posting/fbs/act/create](#operation/PostingAPI_PostingFBSActCreate).

## Ответы

**200** — Статус формирования накладной

- `id` — integer<int64>. Номер задания на формирование документов.
- `status` — string. Cтатус формирования документов: - `FORMING` — ещё не готовы, - `FORMED` — сформированы успешно, - `CONFIRMED` — подписаны Ozon, - `CONFIRMED_WITH_MISMATCH` — подписаны Ozon с расхождениями, - `NOT_FOUND` — документы не найдены, - `UNKNOWN_ERROR` — произошла ошибка.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
