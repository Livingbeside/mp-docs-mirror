---
title: Обновить информацию о доставке сторонней транспортной компанией
api: ozon-seller
method: POST
path: /v1/fbp/order/direct/tpl-dlv/edit
operation_id: FbpOrderDirectTplDlvEdit
tags:
  - OrderDirectFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 32e9a2a4f6b2faba
---

# Обновить информацию о доставке сторонней транспортной компанией

`POST /v1/fbp/order/direct/tpl-dlv/edit`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `row_version` — integer<int64> **обязательный**. Идентификатор актуальной версии черновика.
- `supply_id` — string **обязательный**. Идентификатор заявки на поставку.
- `tracking_number` — string **обязательный**. Трек-номер отправления.
- `transport_company_name` — string **обязательный**. Название транспортной компании.

## Ответы

**200** — Информация обновлена

- `error` — object. Информация об ошибке.
  - `order_errors` — array[string (DELIVERY_DRIVER_NAME_LENGTH_MAXIMUM_REACHED, DELIVERY_VEHICLE_GENRE_LENGTH_MAXIMUM_REACHED, DELIVERY_VEHICLE_REGISTRATION_PLATE_LENGTH_MAXIMUM_REACHED, DELIVERY_TPL_NAME_LENGTH_MAXIMUM_REACHED, DELIVERY_TRACKING_NUMBER_LENGTH_MAXIMUM_REACHED, DELIVERY_DRIVER_NAME_EMPTY, DELIVERY_VEHICLE_GENRE_EMPTY, DELIVERY_VEHICLE_REGISTRATION_PLATE_EMPTY, DELIVERY_TPL_NAME_EMPTY, DELIVERY_TRACKING_NUMBER_EMPTY, DELIVERY_BY_SELLER_EMPTY, DELIVERY_BY_TPL_EMPTY…)]. Тип ошибки: - `DELIVERY_DRIVER_NAME_LENGTH_MAXIMUM_REACHED` — превышена длина ФИО водителя; - `DELIVERY_VEHICLE_GENRE_LENGTH_MAXIMUM_REACHED` — превышена длина типа автомобиля; - `DELIVERY_VEHICLE_REGISTRATION_PLATE_LENGTH_MAXIMUM_REACHED` — превышена длина номера автомобиля; - `DELIVERY_TPL_NAME_LENGTH_MAXIMUM_REACHED` — превышена длина названия сторонней транспортной компании; - `DELIVERY_TRACKING_NUMBER_LENGTH_MAXIMUM_REACHED` — превышена длина трек-номера; - `DELIVERY_DRIVER_NAME_EMPTY` — ФИО водителя не указано; - `DELIVERY_VEHICLE_GENRE_EMPTY` — тип автомобиля не указан; - `DELIVERY_VEHICLE_REGISTRATION_PLATE_EMPTY` — номер автомобиля не указан; - `DELIVERY_TPL_NAME_EMPTY` — название сторонней транспортной компании не указано; - `DELIVERY_TRACKING_NUMBER_EMPTY` — трек-номер не указан; - `DELIVERY_BY_SELLER_EMPTY` — информация о доставке продавцом не указана; - `DELIVERY_BY_TPL_EMPTY` — информация о доставке сторонней транспортной компанией не указана; - `RECEIVE_DATE_NOT_SET` — дата получения не указана; - `SUPPLY_TYPE_NOT_SUPPORTED` — тип поставки не поддерживается; - `INVALID_BUSINESS_FLOW` — неверный бизнес-поток; - `ORDER_LOCKED` — нельзя редактировать товарный состав; - `INVALID_TIMESLOT` — таймслот указан неверно; - `DROP_OFF_DETAILS_EMPTY` — детали drop-off пункта не указаны; - `PICK_UP_ADDRESS_IS_EMPTY` — адрес pick-up точки не указан; - `PICK_UP_SENDER_NAME_IS_EMPTY` — ФИО отправителя не указано; - `PICK_UP_SENDER_PHONE_IS_EMPTY` — номер телефона отправителя не указан; - `PICK_UP_ADDRESS_IS_TOO_LARGE` — превышена длина адреса pick-up точки; - `PICK_UP_SENDER_NAME_IS_TOO_LARGE` — превышена длина ФИО отправителя; - `PICK_UP_SENDER_PHONE_IS_TOO_LARGE` — превышена длина номера телефона отправителя; - `PICK_UP_COMMENT_IS_TOO_LARGE` — превышена длина комментария к поставке; - `PICK_UP_DETAILS_EMPTY` — детали pick-up точки не указаны; - `DROP_OFF_ADDRESS_NOT_SET` — адрес drop-off пункта не указан; - `INVALID_DECLINE_REASON_FOR_WAREHOUSE_TYPE` — причина отмены не подходит для типа склада; - `PICK_UP_SENDER_PHONE_HAS_NOT_ALLOWED_CHARS` — запрещённые символы в номере телефона отправителя; - `TIMESLOT_EMPTY` — таймслот не указан; - `TIMESLOT_EXPIRED` — поставка не доставлена в указанный таймслот; - `BUNDLE_UPDATE_ALREADY_IN_PROGRESS` — обновление информации о поставке уже запущено; - `INVALID_STATE` — неверное состояние.
- `is_error` — boolean. `true`, если есть ошибка.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
