---
title: Получить файл с этикетками
api: ozon-seller
method: POST
path: /v1/posting/fbs/package-label/get
operation_id: PostingAPI_GetLabelBatch
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: 1bb39681f27bb711
---

# Получить файл с этикетками

`POST /v1/posting/fbs/package-label/get`

> ⚠️ Метод помечен как **deprecated**.

C 5 октября 2026 года метод возвращает новые этикетки для отправлений FBS.

[Подробнее о новых этикетках в Базе знаний продавца](https://seller-edu.ozon.ru/libra/fbs/logistics-settings/metody#тестовыи-формат-этикетки)

С 2 ноября 2026 года метод будет отключён. Переключитесь на [/v2/posting/fbs/package-label/get](#operation/PostingFbsPackageLabelGet).

Метод для получения этикеток после вызова [/v1/posting/fbs/package-label/create](#operation/PostingAPI_CreateLabelBatch).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `task_id` — integer<int64> **обязательный**. Номер задания на формирование этикеток из ответа метода [/v1/posting/fbs/package-label/create](#operation/PostingAPI_CreateLabelBatch).

## Ответы

**200** — Статус формирования этикеток или файл с ними

- `result` — object. Результат работы метода.
  - `error` — string. Код ошибки.
  - `file_url` — string. Ссылка на файл с этикетками.
  - `printed_postings_count` — integer<int32>. Количество напечатанных этикеток.
  - `status` — string. Статус формирования этикеток: - `pending` — задание в очереди. - `in_progress` — формируются. - `completed` — файл с этикетками готов. - `error` — ошибка при создании файла.
  - `unprinted_postings` — array[object]. Информация об ошибках, из-за которых не получилось напечатать этикетки.
    - `msg` — string. Причина ошибки.
    - `posting_number` — string. Номер отправления.
  - `unprinted_postings_count` — integer<int32>. Количество этикеток, которые не получилось напечатать.

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
