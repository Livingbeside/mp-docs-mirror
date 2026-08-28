---
title: Получить контактные данные продавца для курьера
api: ozon-seller
method: POST
path: /v1/carriage/courier-contact/get
operation_id: CarriageCourierContactGet
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: bd101066ac9dad51
---

# Получить контактные данные продавца для курьера

`POST /v1/carriage/courier-contact/get`

Возвращает контактные данные продавца, которые добавили или обновили методом [/v1/carriage/courier-contact/set](#operation/CarriageCourierContactSet).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `carriage_id` — integer<int64> **обязательный**. Идентификатор перевозки.

## Ответы

**200** — Контактные данные продавца для курьера

- `contact` — array[object]. Информация о контактах продавца.
  - `carriage_id` — integer<int64>. Идентификатор перевозки.
  - `comment` — string. Комментарий для курьера.
  - `phone` — string. Телефон продавца.
  - `updated_at` — string<date-time>. Дата и время последнего обновления записи в UTC.
  - `wechat_nickname` — string. WeChat продавца.

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
