---
title: Собрать заказ (версия 4)
api: ozon-seller
method: POST
path: /v4/posting/fbs/ship
operation_id: PostingAPI_ShipFbsPostingV4
tags:
  - FBS&rFBSMarks
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9d2bbdc3f71f6755
---

# Собрать заказ (версия 4)

`POST /v4/posting/fbs/ship`

Ответ с кодом 200 не гарантирует успешную сборку заказа. Используйте метод [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3), чтобы проверить, что заказ собран. Если в ответе указан result.substatus = ship_failed, повторите сборку заказа.

Делит заказ на отправления и переводит его в статус `awaiting_deliver`.

Каждый элемент в `packages` может содержать несколько элементов `products` или отправлений. 
Каждый элемент в `products` — это товар, включённый в данное отправление.

Разделить заказ нужно, если:
 - товары не помещаются в одну упаковку,
 - товары нельзя сложить в одну упаковку.
 
Чтобы разделить заказ, передайте в массиве `packages` несколько объектов.

Пример запроса, когда заказ разделять не нужно: 2 товара будут в одном отправлении.
```
{
 "packages": [
 {
 "products": [
 {
 "product_id": 185479045,
 "quantity": 2
 }
 ]
 }
 ],
 "posting_number": "89491381-0072-1"
}
```

Пример запроса, когда заказ нужно разделить: каждый товар будет в отдельном отправлении.

```
{
 "packages": [
 {
 "products": [
 {
 "product_id": 185479045,
 "quantity": 1
 }
 ]
 },
 {
 "products": [
 {
 "product_id": 185479045,
 "quantity": 1
 }
 ]
 }
 ],
 "posting_number": "89491381-0072-1"
} 
``` 

Чтобы внести информацию по экземплярам, используйте метод [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `packages` — ? **обязательный**. Список упаковок. Каждая упаковка содержит список отправлений, на которые делится заказ.
  - `products` — array[object] **обязательный**. Список товаров в отправлении.
    - `product_id` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.
    - `quantity` — integer<int32> **обязательный**. Количество экземпляров.
- `posting_number` — string **обязательный**. Номер отправления.
- `with` — object. Дополнительная информация.
  - `additional_data` — boolean. Чтобы получить дополнительную информацию, передайте `true`.

## Ответы

**200** — Результат сборки заказа

- `additional_data` — ?. Дополнительная информация об отправлениях.
  - `posting_number` — string. Номер отправления.
  - `products` — ?. Список товаров в отправлении.
    - `currency_code` — string. Валюта ваших цен. Cовпадает с валютой, которая установлена в настройках личного кабинета. Возможные значения: - `RUB` — российский рубль, - `BYN` — белорусский рубль, - `KZT` — тенге, - `EUR` — евро, - `USD` — доллар США, - `CNY` — юань.
    - `mandatory_mark` — ?. Обязательная маркировка «Честный ЗНАК».
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — string. Цена.
    - `quantity` — integer<int32>. Количество товара в отправлении.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
- `result` — ?. Результат сборки отправлений.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
