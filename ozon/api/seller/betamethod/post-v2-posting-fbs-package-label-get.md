---
title: Получить файл с этикетками
api: ozon-seller
method: POST
path: /v2/posting/fbs/package-label/get
operation_id: PostingFbsPackageLabelGet
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: cbd3e46cc8762f1b
---

# Получить файл с этикетками

`POST /v2/posting/fbs/package-label/get`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2346-Novye-beta-metody-dlia-raboty-s-etiketkami-FBS/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `task_id` — integer<int64> **обязательный**. Идентификатор задания из ответа метода [/v3/posting/fbs/package-label/create](#operation/PostingFbsPackageLabelCreate).

## Ответы

**200** — Статус формирования этикеток или файл с ними

- `error` — object. Ошибка, которая возникла при формировании этикеток.
  - `code` — string. Код ошибки.
  - `message` — string. Описание ошибки.
- `file_url` — string. Ссылка на файл с этикетками.
- `status` — object. Статус задания.
  - `code` — string. Статус формирования этикеток: - `pending` — задание в очереди; - `in_progress` — формируются; - `completed` — файл с этикетками готов; - `error` — ошибка при создании файла.
  - `postings_count` — integer<int32>. Количество отправлений, по которым запрашивались этикетки.
  - `printed_postings_count` — integer<int32>. Количество отправлений, по которым получилось сгенерировать этикетки.
  - `unprinted_postings` — array[object]. Информация об ошибках, из-за которых не получилось сгенерировать этикетки.
    - `message` — string. Описание ошибки.
    - `posting_number` — string. Номер отправления.

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
