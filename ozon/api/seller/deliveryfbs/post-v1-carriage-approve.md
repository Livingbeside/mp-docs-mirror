---
title: Подтверждение отгрузки
api: ozon-seller
method: POST
path: /v1/carriage/approve
operation_id: CarriageAPI_CarriageApprove
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 59a72fb2bbcb8fa6
---

# Подтверждение отгрузки

`POST /v1/carriage/approve`

Используйте метод, чтобы подтвердить отгрузку после её создания.
После подтверждения отгрузка перейдёт в статус «Сформирована».

После подтверждения отгрузки вы можете получить лист отгрузки методом [/v2/posting/fbs/act/get-pdf](#operation/PostingAPI_PostingFBSGetAct) и штрихкод отгрузки методом [/v2/posting/fbs/act/get-barcode](#operation/PostingAPI_PostingFBSGetBarcode).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `carriage_id` — integer<int64> **обязательный**. Идентификатор отгрузки.
- `containers_count` — integer<int32>. Количество грузовых мест. Используйте параметр, если вы подключены к доверительной приёмке и отгружаете заказы грузовыми местами. Если вы не подключены к доверительной приёмке, пропустите его.

## Ответы

**200** — Отгрузка подтверждена

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
