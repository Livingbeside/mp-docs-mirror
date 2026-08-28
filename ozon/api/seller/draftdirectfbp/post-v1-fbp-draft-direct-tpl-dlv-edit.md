---
title: Редактировать черновик поставки со способом доставки сторонней транспортной компанией
api: ozon-seller
method: POST
path: /v1/fbp/draft/direct/tpl-dlv/edit
operation_id: FbpAPI_FbpDraftDirectTplDlvEdit
tags:
  - DraftDirectFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: fa28ee66b9660116
---

# Редактировать черновик поставки со способом доставки сторонней транспортной компанией

`POST /v1/fbp/draft/direct/tpl-dlv/edit`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `row_version` — integer<int64> **обязательный**. Идентификатор актуальной версии черновика.
- `supply_id` — string **обязательный**. Идентификатор поставки.
- `tracking_number` — string **обязательный**. Трек-номер отправления.
- `transport_company_name` — string **обязательный**. Название транспортной компании.

## Ответы

**200** — Черновик изменён

- `error` — object. Информация об ошибке.
  - `errors` — array[string (ERROR_TYPE_UNSPECIFIED, ORDER_DRAFT_LOCKED, DELIVERY_DRIVER_NAME_LENGTH_MAXIMUM_REACHED, DELIVERY_VEHICLE_GENRE_LENGTH_MAXIMUM_REACHED, DELIVERY_VEHICLE_REGISTRATION_PLATE_LENGTH_MAXIMUM_REACHED, DELIVERY_TPL_NAME_LENGTH_MAXIMUM_REACHED, DELIVERY_TRACKING_NUMBER_LENGTH_MAXIMUM_REACHED, DELIVERY_DRIVER_NAME_EMPTY, DELIVERY_VEHICLE_GENRE_EMPTY, DELIVERY_VEHICLE_REGISTRATION_PLATE_EMPTY, DELIVERY_TPL_NAME_EMPTY, DELIVERY_TRACKING_NUMBER_EMPTY…)]. Тип ошибки: - `ERROR_TYPE_UNSPECIFIED` — не определён; - `ORDER_DRAFT_LOCKED` — черновик заблокирован; - `DELIVERY_DRIVER_NAME_LENGTH_MAXIMUM_REACHED` — превышена длина имени водителя; - `DELIVERY_VEHICLE_GENRE_LENGTH_MAXIMUM_REACHED` — превышена длина типа автомобиля; - `DELIVERY_VEHICLE_REGISTRATION_PLATE_LENGTH_MAXIMUM_REACHED` — превышена длина номера автомобиля; - `DELIVERY_TPL_NAME_LENGTH_MAXIMUM_REACHED` — превышена длина имени стороннего перевозчика; - `DELIVERY_TRACKING_NUMBER_LENGTH_MAXIMUM_REACHED` — превышена длина номера отслеживания; - `DELIVERY_DRIVER_NAME_EMPTY` — ФИО водителя не указано; - `DELIVERY_VEHICLE_GENRE_EMPTY` — тип автомобиля не указан; - `DELIVERY_VEHICLE_REGISTRATION_PLATE_EMPTY` — номер автомобиля не указан; - `DELIVERY_TPL_NAME_EMPTY` — название стороннего перевозчика не указано; - `DELIVERY_TRACKING_NUMBER_EMPTY` — трек-номер не указан; - `INVALID_BUSINESS_FLOW` — неверный бизнес-поток; - `SUPPLY_TYPE_NOT_SUPPORTED` — тип поставки не поддерживается; - `INVALID_STATE` — неверное состояние. По умолчанию: `ERROR_TYPE_UNSPECIFIED`.
- `is_error` — boolean. `true`, если есть ошибка.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
