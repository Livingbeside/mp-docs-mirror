---
title: Добавить или обновить контактные данные продавца для курьера
api: ozon-seller
method: POST
path: /v1/carriage/courier-contact/set
operation_id: CarriageCourierContactSet
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 7d55454e4d95a84b
---

# Добавить или обновить контактные данные продавца для курьера

`POST /v1/carriage/courier-contact/set`

Используйте метод, чтобы добавить или обновить контактные данные продавца, которые передаются курьеру для перевозок с `first_mile_type = pickup` и `integration_type = ozon_outsourced`.
Получите значения параметров `first_mile_type` и `integration_type` в ответе метода [/v1/carriage/get](#operation/CarriageGet).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `carriage_id` — integer<int64> **обязательный**. Идентификатор перевозки.
- `comment` — string. Комментарий для курьера.
- `phone` — string **обязательный**. Телефон продавца.
- `wechat_nickname` — string. WeChat продавца.

## Ответы

**200** — Контактные данные добавлены или обновлены

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
