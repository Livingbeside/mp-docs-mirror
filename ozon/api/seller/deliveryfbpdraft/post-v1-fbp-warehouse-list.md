---
title: Получить список партнёрских складов
api: ozon-seller
method: POST
path: /v1/fbp/warehouse/list
operation_id: FbpWarehouseList
tags:
  - DeliveryFBPDraft
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5de67733d91a58e2
---

# Получить список партнёрских складов

`POST /v1/fbp/warehouse/list`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Список партнёрских складов

- `warehouses` — array[object]. Список складов.
  - `address_detailing` — object. Детали адреса.
    - `city` — string. Город.
    - `country` — string. Страна.
    - `house` — string. Дом.
    - `region` — string. Регион.
    - `street` — string. Улица.
    - `zipcode` — string. Почтовый индекс.
  - `id` — integer<int64>. Идентификатор склада.
  - `is_bonded` — boolean. `true`, если склад бондовый.
  - `name` — string. Название склада.
  - `partner_name` — string. Название партнёра.
  - `supply_types` — array[integer<int32>]. Тип поставки.
  - `timezone_name` — string. Часовой пояс склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
