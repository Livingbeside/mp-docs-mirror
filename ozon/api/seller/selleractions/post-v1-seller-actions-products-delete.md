---
title: Удалить товары из акции
api: ozon-seller
method: POST
path: /v1/seller-actions/products/delete
operation_id: SellerActionsProductsDelete
tags:
  - SellerActions
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 0301686a658500bd
---

# Удалить товары из акции

`POST /v1/seller-actions/products/delete`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1872-Novye-metody-dlia-raboty-s-aktsiiami-sellera) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — integer<uint64> **обязательный**. Идентификатор акции. Получите значение параметра методом [/v1/seller-actions/list](#operation/SellerActionsList).
- `skus` — array[string<uint64>] **обязательный**. Идентификаторы товаров в системе Ozon — SKU.

## Ответы

**200** — Товары удалены

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
