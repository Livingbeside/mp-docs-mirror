---
title: Получить статус включения или отключения транспортных грузомест
api: ozon-seller
method: POST
path: /v1/cargoes/transport/activate/status
operation_id: CargoesTransportActivateStatus
tags:
  - FBOTransport
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f517c98430d319ad
---

# Получить статус включения или отключения транспортных грузомест

`POST /v1/cargoes/transport/activate/status`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2179-Novye-beta-metody-dlia-raboty-s-transportnymi-gruzr/) в сообществе разработчиков Ozon for dev. [Подробнее о работе с транспортными грузоместами](https://dev.ozon.ru/start/525-Rabota-s-transportnymi-gruzomestami-TGM-v-postavkakh-FBO/)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `operation_id` — string **обязательный**. Идентификатор операции из метода [/v1/cargoes/transport/activate](#operation/CargoesTransportActivate).

## Ответы

**200** — Статус

- `error_reasons` — array[string (OPERATION_NOT_FOUND, SUPPLY_IS_FINALIZED, CAN_NOT_EDIT_TAG, UNDEFINED)]. Ошибки при включении или отключении транспортных грузомест: - `OPERATION_NOT_FOUND` — операция не найдена; - `SUPPLY_IS_FINALIZED`, `CAN_NOT_EDIT_TAG` — нельзя изменить поставку; - `UNDEFINED` — неизвестная ошибка.
- `status` — string (SUCCESS, IN_PROGRESS, FAILED). Статус включения или отключения транспортных грузомест: - `SUCCESS` — успешно; - `IN_PROGRESS` — в процессе; - `FAILED` — ошибка.

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
