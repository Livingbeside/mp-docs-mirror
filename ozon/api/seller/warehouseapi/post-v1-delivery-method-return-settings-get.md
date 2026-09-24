---
title: Получить информацию по возвратным настройкам rFBS и rFBS Express
api: ozon-seller
method: POST
path: /v1/delivery-method/return/settings/get
operation_id: GetDeliveryMethodReturnSettingsV1
tags:
  - WarehouseAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 525a5c4583e1ddc2
---

# Получить информацию по возвратным настройкам rFBS и rFBS Express

`POST /v1/delivery-method/return/settings/get`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `delivery_method_id` — integer<int64> **обязательный**. Идентификатор способа доставки. Получите значение параметра методом [/v2/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodListV2).

## Ответы

**200** — Информация получена

- `settings` — object. Информация о возвратных настройках.
  - `courier_details` — object. Настройки курьера.
    - `contact_days` — integer<int32>. Количество дней, за которое вы свяжетесь с покупателем для возврата.
  - `post_office_zipcode` — string. Индекс отделения Почты России для [«лёгкого возврата»](https://seller-edu.ozon.ru/rfbs/vozvraty/vozvraty#«лёгкии-возврат»-почтои-россии).
  - `return_point` — object. Информация о пункте возврата.
    - `address` — string. Адрес пункта возврата.
    - `address_coordinates` — object. Координаты пункта возврата.
      - `latitude` — string. Широта.
      - `longitude` — string. Долгота.
    - `id` — integer<int64>. Идентификатор пункта возврата.
    - `type` — string (UNSPECIFIED, PVZ, PPZ). Тип пункта возврата: - `UNSPECIFIED` — не определён; - `PVZ` — пункт выдачи заказов; - `PPZ` — пункт приёма заказов. По умолчанию: `UNSPECIFIED`.
    - `working_days` — array[object]. Рабочие дни пункта возврата.
      - `day` — string (UNSPECIFIED, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY). Дни недели: - `UNSPECIFIED` — не определён; - `MONDAY` — понедельник; - `TUESDAY` — вторник; - `WEDNESDAY` — среда; - `THURSDAY` — четверг; - `FRIDAY` — пятница; - `SATURDAY` — суббота; - `SUNDAY` — воскресенье. По умолчанию: `UNSPECIFIED`.
      - `from` — string. Время начала.
      - `to` — string. Время окончания.
  - `transport_company_details` — object. Настройки транспортной компании.
    - `transport_company_names` — array[string]. Название транспортной компании.
    - `zipcode` — string. Почтовый индекс транспортной компании.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
