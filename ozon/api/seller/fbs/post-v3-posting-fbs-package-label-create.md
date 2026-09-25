---
title: Создать задание на формирование этикеток
api: ozon-seller
method: POST
path: /v3/posting/fbs/package-label/create
operation_id: PostingFbsPackageLabelCreate
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: dc0c13e5d11377ff
---

# Создать задание на формирование этикеток

`POST /v3/posting/fbs/package-label/create`

Если вы работаете по схеме rFBS или rFBS Express, изучите процесс печати этикетки в [Базе знаний продавца](https://seller-edu.ozon.ru/rfbs/scheme-of-work).

Создаёт задания на асинхронное формирование этикеток для отправлений в статусе «Ожидает отгрузки» — `awaiting_deliver`.
Рекомендуем запрашивать этикетки через 45–60 секунд после сборки заказа.

Чтобы получить созданные этикетки, используйте [/v2/posting/fbs/package-label/get](#operation/PostingFbsPackageLabelGet).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_numbers` — array[string] **обязательный**. Номера отправлений, для которых нужны этикетки.

## Ответы

**200** — Задания на формирование этикеток

- `tasks` — array[object]. Список заданий.
  - `task_id` — integer<int64>. Идентификатор задания. Получите файл с этикетками методом [/v2/posting/fbs/package-label/get](#operation/PostingFbsPackageLabelGet).
  - `task_type` — string. Тип задания: - `big_label` — для обычной этикетки; - `small_label` — для маленькой этикетки.

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
