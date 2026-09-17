---
title: Получить общую информацию о локальности продаж
api: ozon-seller
method: POST
path: /v1/analytics/local-sale/total
operation_id: AnalyticsLocalSaleTotal
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9283821a072491a1
---

# Получить общую информацию о локальности продаж

`POST /v1/analytics/local-sale/total`

Метод соответствует разделу [**Аналитика → Планирование поставок → Локальность продаж**](https://seller.ozon.ru/app/analytics/sales-geography/local-packaging).

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2335-Novye-beta-metody-dlia-polucheniia-lokalnosti-prodazh/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `overpayment_items` — object. Товары с наибольшей переплатой.
  - `count` — integer<int32>. Количество товаров в ответе.
  - `with_top_overpayment_items` — boolean. `true`, чтобы получить товары с наибольшей переплатой.
- `period` — object. Период.
  - `from` — string< YYYY-MM-DD> **обязательный**. Начало периода.
  - `to` — string< YYYY-MM-DD> **обязательный**. Конец периода.

## Ответы

**200** — Информация о локальности продаж

- `fbo_quantity` — integer<int64>. Количество товаров, которые продаются по схеме FBO.
- `local_data` — object. Информация о локальных продажах.
  - `index` — number<double>. Индекс локальных продаж в процентах.
  - `local_quantity` — integer<int64>. Количество товаров, которые доставили локально.
  - `total_quantity` — integer<int64>. Общее количество товаров.
- `overpayment` — object. Информация о переплате по логистике.
  - `delta` — number<double>. Разница с тарифом для локальной продажи.
  - `non_local_delivery` — number<double>. Наценка за нелокальную продажу.
  - `total` — number<double>. Общая переплата.
- `overpayment_items` — array[object]. Товары с наибольшей переплатой.
  - `delivery_schema` — array[string (FBO, FBS)]. Схема продажи: - `FBO`, - `FBS`.
  - `image` — string. Ссылка на изображение товара.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `total_overpayment` — number<double>. Общая переплата по всем товарам.
- `overpayment_reasons` — array[object]. Причины переплат за логистику.
  - `amount` — number<double>. Сумма переплаты.
  - `quantity` — integer<int64>. Количество товаров.
  - `reason` — string (NO_SUPPLIES_TO_CLUSTER, MISSING_ITEMS_IN_CLUSTER, FREQUENT_OUT_OF_STOCK). Причина переплаты: - `NO_SUPPLIES_TO_CLUSTER` — не было поставок в кластер; - `MISSING_ITEMS_IN_CLUSTER` — не все товары поставлялись в кластер; - `FREQUENT_OUT_OF_STOCK` — часто заканчиваются товары.

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
