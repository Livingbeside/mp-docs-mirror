---
title: Связать или отвязать грузоместа и транспортные грузоместа
api: ozon-seller
method: POST
path: /v1/cargoes/transport/bind
operation_id: CargoesTransportBind
tags:
  - FBOTransport
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 0c6b65bcd7a68fba
---

# Связать или отвязать грузоместа и транспортные грузоместа

`POST /v1/cargoes/transport/bind`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2179-Novye-beta-metody-dlia-raboty-s-transportnymi-gruzr/) в сообществе разработчиков Ozon for dev.

[Подробнее о работе с транспортными грузоместами](https://dev.ozon.ru/start/525-Rabota-s-transportnymi-gruzomestami-TGM-v-postavkakh-FBO/)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Грузоместа связаны или отвязаны

- `error_reasons` — array[string (OPERATION_NOT_FOUND, OPERATION_FAILED, SUPPLY_NOT_FOUND, SUPPLY_DOES_NOT_BELONG_TO_COMPANY, SUPPLY_DOES_NOT_BELONG_TO_CONTRACTOR, TRANSPORT_CARGOES_NOT_ENABLED_FOR_SUPPLY, INVALID_SUPPLY_STATE, SUPPLY_IS_FINALIZED, CARGO_IDS_NOT_FOUND, TRANSPORT_CARGO_IDS_NOT_FOUND, ETTN_IS_UPLOADED)]. Ошибки связывания или отвязывания грузомест: - `OPERATION_NOT_FOUND` — операция не найдена; - `OPERATION_FAILED` — операция завершилась с ошибкой; - `SUPPLY_NOT_FOUND` — поставка не найдена; - `SUPPLY_DOES_NOT_BELONG_TO_COMPANY` — заявка на поставку не принадлежит продавцу; - `SUPPLY_DOES_NOT_BELONG_TO_CONTRACTOR` — поставка не принадлежит юридическому лицу; - `TRANSPORT_CARGOES_NOT_ENABLED_FOR_SUPPLY` — для поставки не включены транспортные грузоместа; - `INVALID_SUPPLY_STATE` — неверный статус поставки; - `SUPPLY_IS_FINALIZED` — нельзя редактировать поставку; - `CARGO_IDS_NOT_FOUND` — грузоместа не найдены; - `TRANSPORT_CARGO_IDS_NOT_FOUND` — траспортные грузоместа не найдены; - `ETTN_IS_UPLOADED` — нельзя редактировать поставку с загруженной эТТН.
- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v1/cargoes/transport/bind/status](#operation/CargoesTransportBindStatus).

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
