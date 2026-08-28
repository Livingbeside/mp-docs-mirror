---
title: Создание отгрузки
api: ozon-seller
method: POST
path: /v1/carriage/create
operation_id: CarriageAPI_CarriageCreate
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e3d2a4ab330e0b9d
---

# Создание отгрузки

`POST /v1/carriage/create`

Если вы продавец не из России, обратите внимание на доступность рекомендованного времени в личном кабинете. Используйте метод для создания первой FBS отгрузки. В неё попадут все отправления со статусом «Готов к отгрузке». Созданная отгрузка получит статус `new`. Для отгрузки в статусе `new` можно перезаписать состав отправлений методом [/v1/carriage/set-postings](#operation/CarriageAPI_SetPostings). Если из отгрузки исключить часть отправлений, они могут попасть в следующую отгрузку. Чтобы получить список отправлений в отгрузке, используйте метод [/v2/posting/fbs/act/get-postings](#operation/PostingAPI_ActPostingList).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `all_blr_traceable` — boolean. `true`, если нужно создать отгрузку с прослеживаемыми товарами.
- `delivery_method_id` — integer<int64>. Идентификатор метода доставки.
- `departure_date` — string<date-time>. Дата отгрузки. По умолчанию — текущая дата.

## Ответы

**200** — Информация об отгрузке

- `carriage_id` — integer<int64>. Идентификатор перевозки.

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
