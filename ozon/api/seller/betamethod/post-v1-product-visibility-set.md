---
title: Настроить видимость товара на витрине Ozon и Ozon Селект
api: ozon-seller
method: POST
path: /v1/product/visibility/set
operation_id: ProductVisibilitySet
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9d486824d8052922
---

# Настроить видимость товара на витрине Ozon и Ozon Селект

`POST /v1/product/visibility/set`

Метод доступен продавцам, которые подключены к Ozon Селект или Ozon Доставке.

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1951-Novyi-metod-upravleniia-vidimostiu-na-vitrinakh/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `item_placement` — array[object] **обязательный**. Информация о видимости товара.
  - `placement` — string (OZON, SELECT, OZON_SELECT, NONE) **обязательный**. Платформа для размещения товаров: - `OZON` — только на Ozon. - `SELECT` — только на Селект. [Подробнее об Ozon Селект в Базе знаний продавца](https://seller-edu.ozon.ru/libra/ozon-select) - `OZON_SELECT` — на Селект и Ozon. - `NONE` — товар скрыт везде. Только для продавцов, которые работают через Ozon Доставку. [Подробнее об Ozon Доставке в Базе знаний продавца](https://seller-edu.ozon.ru/libra/ozon-logistika/osobennosti-raboty#что-такое-ozon-доставка)
  - `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.

## Ответы

**200** — Видимость товара настроена

- `items` — array[object]. Информация о видимости товаров.
  - `select_permission` — string (UNSPECIFIED, RESTRICTED, ALLOWED). Возможность продажи товара на Ozon Селект: - `UNSPECIFIED` — не определено; - `RESTRICTED` — товар нельзя продавать; - `ALLOWED` — товар можно продавать. По умолчанию: `UNSPECIFIED`.
  - `seller_item_placement` — string (UNSPECIFIED, OZON, SELECT, OZON_SELECT, NONE). Значение видимости, которое установил продавец: - `UNSPECIFIED` — не определено; - `OZON` — только на Ozon; - `SELECT` — только на Селект; - `OZON_SELECT` — на Селект и Ozon; - `NONE` — товар скрыт везде. По умолчанию: `UNSPECIFIED`.
  - `seller_item_placement_list` — array[string (UNSPECIFIED, OZON, SELECT)]. Список значений видимости, которые установил продавец: - `UNSPECIFIED` — не определено; - `OZON` — только на Ozon; - `SELECT` — только на Селект.
  - `showcases_visibility` — string (UNSPECIFIED, OZON, SELECT, OZON_SELECT, NONE). На каких витринах показывается товар: - `UNSPECIFIED` — не определено; - `OZON` — только на Ozon; - `SELECT` — только на Селект; - `OZON_SELECT` — на Селект и Ozon; - `NONE` — товар скрыт везде. По умолчанию: `UNSPECIFIED`.
  - `showcases_visibility_list` — array[string (UNSPECIFIED, OZON, SELECT)]. Список витрин, на которых показывается товар: - `UNSPECIFIED` — не определено; - `OZON` — только на Ozon; - `SELECT` — только на Селект.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `warnings` — array[string]. Предупреждения.
- `items_errors` — array[object]. Товары с ошибками.
  - `code` — string. Код ошибки.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
