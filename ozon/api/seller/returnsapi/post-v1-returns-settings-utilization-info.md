---
title: Получить настройки автоутилизации
api: ozon-seller
method: POST
path: /v1/returns/settings/utilization/info
operation_id: UtilizationInfo
tags:
  - ReturnsAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 700da0ca081b8ff1
---

# Получить настройки автоутилизации

`POST /v1/returns/settings/utilization/info`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Настройки автоутилизации

- `min_price` — object. Минимальная цена товара, с которой можно установить автоутилизацию методом [/v1/returns/settings/utilization/update](#operation/UtilizationUpdate).
  - `amount` — string. Сумма.
  - `currency` — string. Валюта.
- `utilization_settings` — object. Настройки утилизации.
  - `utilization_price` — object. Максимальная цена автоутилизации для товаров без дефектов.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `utilization_price_defects` — object. Максимальная цена автоутилизации для товаров с дефектами.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
