---
title: Добавить или обновить товары в автодобавлении в акцию
api: ozon-seller
method: POST
path: /v2/actions/auto-add/products/update
operation_id: ActionsAutoAddProductsUpdateV2
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f142ffcdd21ce579
---

# Добавить или обновить товары в автодобавлении в акцию

`POST /v2/actions/auto-add/products/update`

До 13 октября 2026 года метод работает аналогично [/v1/actions/auto-add/products/update](#operation/ActionsAutoAddProductsUpdate), изменить цену на карточке товара с помощью метода не получится.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — integer<uint64> **обязательный**. Идентификатор акции.
- `auto_add_date` — string<date-time> **обязательный**. Дата и время автодобавления товаров в акцию из параметра `result.auto_add_dates` в ответе метода [/v1/actions](#operation/Promos).
- `products` — array[object] **обязательный**. Список товаров, которые нужно добавить или обновить в автодобавлении.
  - `action_price` — object. Предельная цена товара. Изменим предельную цену в карточке товара в дату `auto_add_date`, даже если предельная цена была установлена ранее. Если значение меньше или равно лимиту акции «Эластичный бустинг» или «Максимальный бустинг» — добавим товар в акцию, если больше — удалим товар из акции.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `id` — integer<uint64>. Идентификатор товара.
  - `stock` — integer<uint64>. Количество единиц товара в акции для акции «Промокоды». Не указывайте для акций «Эластичный бустинг» и «Максимальный бустинг».

## Ответы

**200** — Товары добавлены или обновлены в автодобавлении

- `below_min_price` — array[object]. Список товаров с ценой ниже минимальной.
  - `key` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `value` — number<double>. Цена товара.
- `deactivated_ids` — array[string<uint64>]. Идентификаторы товаров, которые удалены из акции.
- `extremely_low_price` — array[object]. Список товаров со скидкой больше 70%.
  - `key` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `value` — number<double>. Цена товара.
- `failed_price` — array[object]. Список товаров, которые не прошли валидацию по цене.
  - `key` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `value` — number<double>. Значение проблемной цены: - максимальная цена товара для автодобавления в акцию, если цена товара её превышает; - цена со скидкой 95%, если скидка на товар больше 95%.
- `product_ids` — array[string<uint64>]. Идентификаторы товаров, которые получилось добавить или обновить.
- `rejected` — array[object]. Идентификаторы товаров, которые не получилось добавить или обновить.
  - `product_id` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `reason` — string. Причина, по которой не получилось добавить или обновить товар.
- `warnings` — array[object]. Список предупреждений по товарам.
  - `product_id` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `reason` — string. Предупреждение.

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
