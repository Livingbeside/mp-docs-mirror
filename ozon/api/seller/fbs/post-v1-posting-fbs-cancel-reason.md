---
title: Причины отмены отправления
api: ozon-seller
method: POST
path: /v1/posting/fbs/cancel-reason
operation_id: PostingAPI_GetPostingFbsCancelReasonV1
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: fb5ede59e48c99b3
---

# Причины отмены отправления

`POST /v1/posting/fbs/cancel-reason`

Возвращает список причин отмены для конкретных отправлений.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `related_posting_numbers` — array[string] **обязательный**. Номера отправлений.

## Ответы

**200** — Причины отмены отправлений

- `result` — array[object]. Результат запроса.
  - `posting_number` — string. Номер отправления.
  - `reasons` — array[object]. Информация о причинах отмены.
    - `id` — integer<int64>. Идентификатор причины отмены: - `352` — товар закончился на складе продавца. - `400` — остался только бракованный товар. - `401` — продавец отклонил арбитраж. - `402` — другое (вина продавца). - `665` — покупатель не забрал заказ. - `666` — возврат из службы доставки: нет доставки в указанный регион. - `667` — заказ утерян службой доставки.
    - `title` — string. Описание причины отмены.
    - `type_id` — string. Инициатор отмены отправления: - `buyer` — покупатель, - `seller` — продавец.

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
