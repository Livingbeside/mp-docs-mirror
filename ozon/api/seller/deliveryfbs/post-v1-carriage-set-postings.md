---
title: Изменение состава отгрузки
api: ozon-seller
method: POST
path: /v1/carriage/set-postings
operation_id: CarriageAPI_SetPostings
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: aed8434ffb3f3401
---

# Изменение состава отгрузки

`POST /v1/carriage/set-postings`

Метод недоступен для продавцов из СНГ. Полностью перезаписывает список заказов в отгрузке. Передавайте только те заказы, которые находятся в статусе Ожидает отгрузки , и вы готовы их отгрузить. Менять состав можно только у отгрузок со статусом `new`. Чтобы вернуться к списку заказов, удалите отгрузку с помощью метода /v1/carriage/cancel , и создайте новую.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `carriage_id` — integer<int64> **обязательный**. Идентификатор отгрузки.
- `posting_numbers` — array[string] **обязательный**. Актуальный список отправлений.

## Ответы

**200** — Информация об отправлении

- `result` — ?
  - `error` — string. Описание ошибки.
  - `posting_number` — string. Номер отправления.
  - `result` — boolean. Результат обработки запроса. `true`, если запрос был обработан успешно.

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
