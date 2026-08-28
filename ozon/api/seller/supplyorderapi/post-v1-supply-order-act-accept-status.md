---
title: Получить статус согласования акта
api: ozon-seller
method: POST
path: /v1/supply-order/act/accept/status
operation_id: SupplyOrderActAcceptStatus
tags:
  - SupplyOrderAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: daa1a0919f7b4b26
---

# Получить статус согласования акта

`POST /v1/supply-order/act/accept/status`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2294-Novye-beta-metody-dlia-raboty-s-aktami-FBO/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `operation_id` — string **обязательный**. Идентификатор операции из метода [/v1/supply-order/act/accept](#operation/SupplyOrderActAccept).

## Ответы

**200** — Статус согласования акта

- `error_message` — string. Причина ошибки.
- `status` — string (SUCCESS, IN_PROGRESS, FAILED). Статус операции: - `SUCCESS` — акт согласован; - `IN_PROGRESS` — согласование в процессе; - `FAILED` — ошибка при согласовании акта. По умолчанию: `SUCCESS`.

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
