---
title: Обновить информацию о доставке силами продавца
api: ozon-seller
method: POST
path: /v1/fbp/order/direct/seller-dlv/edit
operation_id: FbpAPI_FbpOrderDirectSellerDlvEdit
tags:
  - OrderDirectFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 1a71b73e793299a1
---

# Обновить информацию о доставке силами продавца

`POST /v1/fbp/order/direct/seller-dlv/edit`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `driver_name` — string **обязательный**. ФИО водителя.
- `row_version` — integer<int64> **обязательный**. Идентификатор актуальной версии черновика.
- `supply_id` — string **обязательный**. Идентификатор заявки на поставку.
- `vehicle_number` — string **обязательный**. Номер автомобиля.
- `vehicle_type` — string **обязательный**. Тип автомобиля.

## Ответы

**200** — Информация обновлена

- `error` — object. Информация об ошибке.
  - `order_errors` — array[string (ERROR_TYPE_UNSPECIFIED, DELIVERY_DRIVER_NAME_LENGTH_MAXIMUM_REACHED, DELIVERY_VEHICLE_GENRE_LENGTH_MAXIMUM_REACHED, DELIVERY_VEHICLE_REGISTRATION_PLATE_LENGTH_MAXIMUM_REACHED, DELIVERY_TPL_NAME_LENGTH_MAXIMUM_REACHED, DELIVERY_TRACKING_NUMBER_LENGTH_MAXIMUM_REACHED, DELIVERY_DRIVER_NAME_EMPTY, DELIVERY_VEHICLE_GENRE_EMPTY, DELIVERY_VEHICLE_REGISTRATION_PLATE_EMPTY, DELIVERY_TPL_NAME_EMPTY, DELIVERY_TRACKING_NUMBER_EMPTY, DELIVERY_BY_SELLER_EMPTY…)]. Тип ошибки: - `ERROR_TYPE_UNSPECIFIED` — не определён; - `DELIVERY_DRIVER_NAME_LENGTH_MAXIMUM_REACHED` — превышена длина ФИО водителя; - `DELIVERY_VEHICLE_GENRE_LENGTH_MAXIMUM_REACHED` — превышена длина типа автомобиля; - `DELIVERY_VEHICLE_REGISTRATION_PLATE_LENGTH_MAXIMUM_REACHED` — превышена длина номера автомобиля; - `DELIVERY_TPL_NAME_LENGTH_MAXIMUM_REACHED` — превышена длина названия стороннего перевозчика; - `DELIVERY_TRACKING_NUMBER_LENGTH_MAXIMUM_REACHED` — превышена длина трек-номера отслеживания; - `DELIVERY_DRIVER_NAME_EMPTY` — ФИО водителя не указано; - `DELIVERY_VEHICLE_GENRE_EMPTY` — тип автомобиля не указан; - `DELIVERY_VEHICLE_REGISTRATION_PLATE_EMPTY` — номер автомобиля не указан; - `DELIVERY_TPL_NAME_EMPTY` — название стороннего перевозчика не указано; - `DELIVERY_TRACKING_NUMBER_EMPTY` — трек-номер не указан; - `SUPPLY_TYPE_NOT_SUPPORTED` — тип поставки не поддерживается; - `INVALID_BUSINESS_FLOW` — неверный бизнес-поток; - `ORDER_LOCKED` — нельзя редактировать товарный состав; - `INVALID_TIMESLOT` — таймслот не указан или указан неверно; - `DROP_OFF_DETAILS_EMPTY` — детали drop-off пункта не указаны; - `PICK_UP_ADDRESS_IS_EMPTY` — детали адреса точки забора не указаны; - `PICK_UP_SENDER_NAME_IS_EMPTY` — ФИО отправителя не указано; - `PICK_UP_SENDER_PHONE_IS_EMPTY` — номер телефона отправителя не указан; - `PICK_UP_ADDRESS_IS_TOO_LARGE` — превышена длина адреса точки забора; - `PICK_UP_SENDER_NAME_IS_TOO_LARGE` — превышена длина ФИО отправителя; - `PICK_UP_SENDER_PHONE_IS_TOO_LARGE` — превышена длина номера телефона отправителя; - `PICK_UP_COMMENT_IS_TOO_LARGE` — превышена длина комментария к поставке; - `PICK_UP_DETAILS_EMPTY` — детали точки забора не указаны; - `DROP_OFF_ADDRESS_NOT_SET` — не указан адрес drop-off пункта; - `INVALID_STATE` — неверное состояние. По умолчанию: `ERROR_TYPE_UNSPECIFIED`.
- `is_error` — boolean. `true`, если есть ошибка.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
