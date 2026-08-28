---
title: Получить информацию о товарах в акте
api: ozon-seller
method: POST
path: /v1/supply-order/act/product/get
operation_id: SupplyOrderActProductGet
tags:
  - SupplyOrderAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 1b519552f9a9aa18
---

# Получить информацию о товарах в акте

`POST /v1/supply-order/act/product/get`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2294-Novye-beta-metody-dlia-raboty-s-aktami-FBO/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `supply_id` — integer<int64> **обязательный**. Идентификатор поставки.

## Ответы

**200** — Информация о товарах в акте

- `skus_defects` — array[object]. Список товаров с браком.
  - `defect_reasons` — array[string]. Причины брака.
  - `sku` — integer<int64>. Идентификатор товара.
- `supply_acts` — array[object]. Список актов в поставке.
  - `act_id` — integer<int64>. Идентификатор акта.
  - `items` — array[object]. Список товаров в акте.
    - `approved_amount` — object. Согласованная стоимость товаров.
      - `amount` — object. Сумма с НДС.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
      - `amount_vat` — object. Сумма НДС.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
      - `amount_without_vat` — object. Сумма без НДС.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
    - `approved_quantity` — integer<int32>. Количество согласованного товара в акте.
    - `declared_quantity` — integer<int32>. Количество заявленного товара в акте.
    - `fact_amount` — object. Фактическая стоимость товаров.
      - `amount` — object. Сумма с НДС.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
      - `amount_vat` — object. Сумма НДС.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
      - `amount_without_vat` — object. Сумма без НДС.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
    - `fact_quantity` — integer<int32>. Количество принятого товара.
    - `sku_info` — object. Информация о товаре.
      - `barcode` — string. Штрихкод товара.
      - `image_link` — string. Ссылка на изображение товара.
      - `name` — string. Название товара.
      - `offer_id` — string. Артикул товара.
      - `price_without_vat` — object. Цена товара без НДС.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
      - `sku` — integer<int64>. Идентификатор товара.
      - `vat` — number<float>. Ставка НДС.
  - `type` — string (UNSPECIFIED, ACCEPTANCE, DEFECT, SURPLUS, SHORTCOMING). Тип акта: - `UNSPECIFIED` — не определён; - `ACCEPTANCE` — акт приёмки; - `DEFECT` — акт о браке; - `SURPLUS` — акт об излишках; - `SHORTCOMING` — акт о недостаче. По умолчанию: `UNSPECIFIED`.
  - `unidentified_quantity` — integer<int32>. Количество неопознанных излишков.
- `supply_id` — integer<int64>. Идентификатор поставки.

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
