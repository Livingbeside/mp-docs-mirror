---
title: Добавить или обновить товар в акции
api: ozon-seller
method: POST
path: /v1/actions/products/update
operation_id: ActionsProductsUpdate
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 1427ff77cbdf2c54
---

# Добавить или обновить товар в акции

`POST /v1/actions/products/update`

До 13 октября 2026 года метод работает аналогично [/v1/actions/products/activate](#operation/PromosProductsActivate), изменить цену на карточке товара с помощью метода не получится.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — integer<uint64> **обязательный**. Идентификатор акции. Получите методом [/v1/actions](#operation/Promos).
- `products` — array[object] **обязательный**. Список товаров.
  - `action_price` — object **обязательный**. Предельная цена товара. Если добавляете товар вне акции «Промокоды», изменим предельную цену в карточке товара, даже если она была установлена ранее. Если значение меньше или равно лимиту акции «Эластичный бустинг» или «Максимальный бустинг» — добавим товар в акцию, если больше — удалим товар из акции.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `product_id` — integer<uint64> **обязательный**. Идентификатор товара в системе Ozon — `product_id`.
  - `stock` — integer<uint64>. Количество единиц товара в акции «Промокоды». Не передавайте параметр для акций «Эластичный бустинг» и «Максимальный бустинг».

## Ответы

**200** — Товары добавлены или обновлены

- `active_product_ids` — array[string<uint64>]. Список идентификаторов товаров, которые добавлены в акцию.
- `deactivated_product_ids` — array[string<uint64>]. Список идентификаторов товаров, которые удалены из акции.
- `rejected` — array[object]. Список товаров, которые не удалось добавить в акцию.
  - `product_id` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `reason` — string. Причина, по которой товар не добавлен в акцию.
- `warnings` — array[object]. Информация о причинах, из-за которых товары удалены из акции.
  - `product_id` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `reason` — string. Причина, по которой товар удалён из акции.

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
