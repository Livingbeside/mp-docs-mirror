---
title: Удалить грузоместа и транспортные грузоместа в заявке на поставку
api: ozon-seller
method: POST
path: /v2/cargoes/delete
operation_id: CargoesDeleteV2
tags:
  - FBOTransport
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: aadef51ac7b3f821
---

# Удалить грузоместа и транспортные грузоместа в заявке на поставку

`POST /v2/cargoes/delete`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2179-Novye-beta-metody-dlia-raboty-s-transportnymi-gruzr/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Грузоместа и транспортные грузоместа удалены

- `errors` — object. Ошибки.
  - `cargo_error_reasons` — array[object]. Ошибки при удалении грузомест.
    - `cargo_id` — integer<int64>. Идентификатор грузоместа.
    - `error_reasons` — array[string (UNSPECIFIED, CARGO_NOT_FOUND)]. Список ошибок грузоместа: - `UNSPECIFIED` — не определена; - `CARGO_NOT_FOUND` — грузоместо не найдено.
  - `supply_error_reasons` — array[string (UNSPECIFIED, SUPPLY_NOT_FOUND, CANT_DELETE_ALL_CARGOES, SUPPLY_DOES_NOT_BELONG_TO_THE_CONTRACTOR, SUPPLY_DOES_NOT_BELONG_TO_THE_COMPANY, SUPPLY_CARGOES_IS_FINALIZED, SUPPLY_CARGOES_LOCKED, OPERATION_NOT_FOUND, ETTN_IS_UPLOADED, CANT_DELETE_ALL_TRANSPORT_CARGOES, UNDEFINED)]. Ошибки поставки: - `UNSPECIFIED` — не определена; - `SUPPLY_NOT_FOUND` — поставка не найдена; - `CANT_DELETE_ALL_CARGOES` — нельзя удалять все грузоместа; - `SUPPLY_DOES_NOT_BELONG_TO_THE_CONTRACTOR` — не принадлежит вашему юридическому лицу; - `SUPPLY_DOES_NOT_BELONG_TO_THE_COMPANY` — не принадлежит вашему кабинету; - `SUPPLY_CARGOES_IS_FINALIZED` — грузоместа поставки нельзя редактировать; - `SUPPLY_CARGOES_LOCKED` — другой процесс блокирует редактирование грузомест поставки; - `OPERATION_NOT_FOUND` — операция не найдена; - `ETTN_IS_UPLOADED` — электронная ТТН загружена; - `CANT_DELETE_ALL_TRANSPORT_CARGOES` — нельзя удалять все транспортные грузоместа; - `UNDEFINED` — неизвестная ошибка.
  - `transport_cargo_error_reasons` — array[object]. Ошибки при удалении транспортных грузомест.
    - `error_reasons` — array[string (UNSPECIFIED, CARGO_NOT_FOUND)]. Список ошибок транспортного грузоместа: - `UNSPECIFIED` — не определена; - `CARGO_NOT_FOUND` — транспортное грузоместо не найдено.
    - `transport_cargo_id` — integer<int64>. Идентификатор транспортного грузоместа.
- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v2/cargoes/delete/status](#operation/CargoesDeleteStatusV2).

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
