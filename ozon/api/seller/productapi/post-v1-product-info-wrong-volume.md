---
title: Список товаров с некорректными ОВХ
api: ozon-seller
method: POST
path: /v1/product/info/wrong-volume
operation_id: ProductAPI_ProductInfoWrongVolume
tags:
  - ProductAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 00a9cae923296c63
---

# Список товаров с некорректными ОВХ

`POST /v1/product/info/wrong-volume`

Возвращает список товаров с некорректными объёмно-весовыми характеристиками (ОВХ). Если вы указали размеры правильно, обратитесь в поддержку Ozon.

[Подробнее об объёмно-весовых характеристиках в Базе знаний продавца](https://seller-edu.ozon.ru/libra/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/ovh)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `limit` — integer<int64> **обязательный**. Максимальное количество элементов в ответе.

## Ответы

**200** — Информация о товарах с некорректными ОВХ

- `cursor` — string. Указатель для выборки следующих данных.
- `products` — ?. Список товаров.
  - `height` — integer<int64>. Высота товара.
  - `length` — integer<int64>. Длина товара.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `weight` — integer<int64>. Вес товара в упаковке.
  - `width` — integer<int64>. Ширина товара.

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
