---
title: Добавить или обновить товары в автодобавлении в акцию
api: ozon-seller
method: POST
path: /v1/actions/auto-add/products/update
operation_id: ActionsAutoAddProductsUpdate
tags:
  - PromosBeta
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 1d4a25bd4768e449
---

# Добавить или обновить товары в автодобавлении в акцию

`POST /v1/actions/auto-add/products/update`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2009-Novye-metody-dlia-upravleniia-avtodobavleniem-tovarov-v-aktsii/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — integer<uint64>. Идентификатор акции.
- `auto_add_date` — string<date-time>. Дата и время автодобавления товаров в акцию из параметра `result.auto_add_dates` в ответе метода [/v1/actions](#operation/Promos).
- `to_update` — array[object]. Список товаров, которые нужно добавить или обновить в автодобавлении.
  - `action_price` — number<double>. Цена товара по акции.
  - `currency` — string. Валюта цены.
  - `product_id` — integer<uint64>. Идентификатор товара, который нужно добавить или обновить.
  - `quantity` — integer<uint64>. Количество товаров в акции.

## Ответы

**200** — Товары добавлены или обновлены в автодобавлении

- `below_min_price` — array[object]. Список товаров с ценой ниже минимальной.
  - `key` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `value` — number<double>. Цена товара.
- `extremely_low_price` — array[object]. Список товаров со скидкой больше 70%.
  - `key` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `value` — number<double>. Цена товара.
- `failed_price` — array[object]. Список товаров, которые не прошли валидацию по цене.
  - `key` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `value` — number<double>. Значение проблемной цены: - Если цена товара больше `max_discount_price` — значение параметра `max_discount_price`; - Если скидка на товар больше 95% — цена со скидкой 95%.
- `rejected` — array[object]. Идентификаторы товаров, которые не получилось добавить или обновить.
  - `code` — string (NOT_FOUND, NO_CHANGES, STOCK_REQUIRED, INVALID_ACTION_PRICE, MAX_ACTION_PRICE, REJECTED_LOW_PRICE, INVALID_CURRENCY). Код ошибки: - `NOT_FOUND` — товар не найден; - `NO_CHANGES` — нет изменений; - `STOCK_REQUIRED` — остатков товара не хватит для акции; - `INVALID_ACTION_PRICE` — некорректная цена по акции; - `MAX_ACTION_PRICE` — цена по акции выше максимальной; - `REJECTED_LOW_PRICE` — цена по акции ниже минимальной; - `INVALID_CURRENCY` — некорректная валюта.
  - `product_id` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `reason` — string. Причина, по которой не получилось добавить или обновить товар.
- `updated_ids` — array[string<uint64>]. Идентификаторы товаров, которые получилось добавить или обновить.

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
