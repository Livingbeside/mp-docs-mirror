---
title: Получить список складов продавца
api: ozon-seller
method: POST
path: /v1/warehouse/fbo/seller/list
operation_id: WarehouseFboSellerList
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 78075344e6ff7390
---

# Получить список складов продавца

`POST /v1/warehouse/fbo/seller/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Список складов

- `warehouses` — array[object]. Список складов продавца.
  - `address` — object. Информация об адресе склада продавца.
    - `address` — string. Адрес.
    - `city` — string. Город.
    - `coordinates` — object. Координаты.
      - `latitude` — number<double>. Широта.
      - `longitude` — number<double>. Долгота.
    - `country_code` — string. Код страны в формате ISO 2.
    - `macrolocal_cluster_id` — integer<int64>. Идентификатор кластера размещения.
    - `region` — string. Регион.
    - `timezone` — string. Часовой пояс.
  - `contacts` — object. Контакты.
    - `phone_numbers` — array[string]. Номера телефонов.
  - `courier_comment` — string. Комментарий для курьера.
  - `is_active` — boolean. `true`, если склад активный.
  - `is_pickup` — boolean. `true`, если доступна отгрузка курьером.
  - `seller_warehouse_id` — integer<int64>. Идентификатор склада продавца.
  - `seller_warehouse_name` — string. Название склада продавца.
  - `working_days` — array[object]. Рабочие дни склада продавца.
    - `day` — string (UNSPECIFIED, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY). Рабочий день: - `UNSPECIFIED` — не определён, - `MONDAY` — понедельник, - `TUESDAY` — вторник, - `WEDNESDAY` — среда, - `THURSDAY` — четверг, - `FRIDAY` — пятница, - `SATURDAY` — суббота, - `SUNDAY` — воскресенье. По умолчанию: `UNSPECIFIED`.
    - `time_from_local` — string. Время начала работы.
    - `time_to_local` — string. Время окончания работы.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
