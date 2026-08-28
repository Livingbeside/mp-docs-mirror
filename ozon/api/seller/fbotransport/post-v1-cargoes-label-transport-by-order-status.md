---
title: Получить статус генерации этикеток для транспортных грузомеcт по идентификатору поставки
api: ozon-seller
method: POST
path: /v1/cargoes/label/transport-by-order/status
operation_id: CargoesLabelTransportByOrderStatus
tags:
  - FBOTransport
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d8e8b3f3857a288a
---

# Получить статус генерации этикеток для транспортных грузомеcт по идентификатору поставки

`POST /v1/cargoes/label/transport-by-order/status`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2179-Novye-beta-metody-dlia-raboty-s-transportnymi-gruzr/) в сообществе разработчиков Ozon for dev.

[Подробнее о работе с транспортными грузоместами](https://dev.ozon.ru/start/525-Rabota-s-transportnymi-gruzomestami-TGM-v-postavkakh-FBO/)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `operation_id` — string **обязательный**. Идентификатор операции из метода [/v1/cargoes/label/transport-by-order/create](#operation/CargoesLabelTransportByOrderCreate).

## Ответы

**200** — Статус

- `error_reasons` — array[string (ORDER_NOT_FOUND, OPERATION_NOT_FOUND, OPERATION_FAILED, ALL_SUPPLIES_SKIPPED, LABELS_COUNT_EXCEED, UNDEFINED)]. Ошибки при генерации этикеток транспортных грузомест: - `ORDER_NOT_FOUND` — заявка не найдена; - `OPERATION_NOT_FOUND` — операция не найдена; - `OPERATION_FAILED` — операция завершилась с ошибкой; - `ALL_SUPPLIES_SKIPPED` — нет этикеток для поставок; - `LABELS_COUNT_EXCEED` — превышено количество генерируемых этикеток; - `UNDEFINED` — неизвестная ошибка.
- `result` — object. Этикетки транспортных грузомест.
  - `file_url` — string. Ссылка на PDF-файл с этикетками.
  - `skipped_supplies_ids` — array[string<int64>]. Поставки, по которым не сгенерированы этикетки.
- `status` — string (SUCCESS, IN_PROGRESS, FAILED). Статус генерации этикеток: - `SUCCESS` — успешно; - `IN_PROGRESS` — в процессе; - `FAILED` — ошибка.

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
