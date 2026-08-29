---
title: Получить контент-рейтинг товаров по SKU
api: ozon-seller
method: POST
path: /v1/product/rating-by-sku
operation_id: ProductAPI_GetProductRatingBySku
tags:
  - ProductAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ccfa8c4949b7d777
---

# Получить контент-рейтинг товаров по SKU

`POST /v1/product/rating-by-sku`

Метод для получения контент-рейтинга товаров, а также рекомендаций по его увеличению.

[Подробнее о контент-рейтинге](https://seller-edu.ozon.ru/docs/work-with-goods/content-rating.html)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `skus` — ? **обязательный**. Идентификаторы товаров в системе Ozon — SKU, для которых нужно вернуть контент-рейтинг.

## Ответы

**200** — Контент-рейтинг товаров

- `products` — ?. Контент-рейтинг товаров.
  - `sku` — integer<int64>. Идентификатор товара на Ozon.
  - `rating` — number<float>. Контент-рейтинг товара: от 0 до 100.
  - `groups` — ?. Группы характеристик, из которых складывается контент-рейтинг.
    - `conditions` — ?. Список условий, увеличивающих контент-рейтинг товара.
      - `cost` — number<float>. Количество баллов контент-рейтинга, которое даёт выполнение условия.
      - `description` — string. Описание условия.
      - `fulfilled` — boolean. Признак, что условие выполнено.
      - `key` — string. Идентификатор условия.
    - `improve_at_least` — integer. Количество атрибутов, которые нужно заполнить для получения максимального балла в этой группе характеристик.
    - `improve_attributes` — ?. Cписок атрибутов, заполнение которых может увеличить контент-рейтинг товара.
      - `id` — integer<int64>. Идентификатор атрибута.
      - `name` — string. Название атрибута.
    - `key` — string. Идентификатор группы.
    - `name` — string. Название группы.
    - `rating` — number<float>. Рейтинг в группе.
    - `weight` — number<float>. Процент влияния характеристик группы на контент-рейтинг.

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
