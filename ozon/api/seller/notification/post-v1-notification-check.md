---
title: Проверить URL-адрес для уведомлений
api: ozon-seller
method: POST
path: /v1/notification/check
operation_id: CheckNotification
tags:
  - Notification
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 3580c9979a826062
---

# Проверить URL-адрес для уведомлений

`POST /v1/notification/check`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1978-Novye-beta-metody-dlia-upravleniia-podkliucheniiami-PUSH-uvedomlenii/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `url` — string **обязательный**. URL-адрес.

## Ответы

**200** — Результат проверки

- `errors` — array[object]. Ошибки, возникшие при проверке.
  - `description` — string. Описание ошибки.
  - `type` — string (REQUEST_ERROR, REQUEST_TIMEOUT, SERVER_FAULT, STATUS_CODE_NOT_OK, EMPTY_BODY, INVALID_BODY, INVALID_JSON, WRONG_RESULT_FIELD, WRONG_RESULT_TIME_FIELD). Тип ошибки: - `REQUEST_ERROR` — нет подключения по URL-адресу; - `REQUEST_TIMEOUT` — превышено время ожидания запроса; - `SERVER_FAULT` — сервис вернул внутреннюю ошибку; - `STATUS_CODE_NOT_OK` — HTTP-статус ответа не `200`; - `EMPTY_BODY` — тело ответа пустое или отсутствует; - `INVALID_BODY` — некорректный формат тела ответа; - `INVALID_JSON` — ошибка при разборе или валидации JSON-данных; - `WRONG_RESULT_FIELD` — сервис вернул тело ответа не по шаблону; - `WRONG_RESULT_TIME_FIELD` — параметр `time` в теле ответа некорректный.
- `is_active` — boolean **обязательный**. `true`, если URL-адрес активен.

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
