---
title: Дерево категорий и типов товаров
api: ozon-seller
method: POST
path: /v1/description-category/tree
operation_id: DescriptionCategoryAPI_GetTree
tags:
  - CategoryAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f3e2b1d5ba6a9ad4
---

# Дерево категорий и типов товаров

`POST /v1/description-category/tree`

Возвращает категории и типы для товаров в виде дерева. Создание товаров доступно только в категориях последнего уровня, сравните именно их с категориями на своей площадке. Категории не создаются по запросу пользователя. Внимательно выбирайте категорию для товара: для разных категорий применяется разный размер комиссии.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `language` — string (DEFAULT, RU, EN, TR, ZH_HANS). Язык в ответе: - `EN` — английский, - `RU` — русский, - `TR` — турецкий, - `ZH_HANS` — китайский. По умолчанию используется русский язык. По умолчанию: `DEFAULT`.

## Ответы

**200** — Дерево категорий

- `result` — array[object]. Список категорий.
  - `description_category_id` — integer<int64>. Идентификатор категории.
  - `category_name` — string. Название категории.
  - `children` — array[object]. Дерево подкатегорий.
    - `description_category_id` — integer<int64>. Идентификатор категории.
    - `category_name` — string. Название категории.
    - `children` — array[object]. Дерево подкатегорий.
      - `description_category_id` — integer<int64>. Идентификатор категории.
      - `category_name` — string. Название категории.
      - `children` — array[object]. Дерево подкатегорий.
        - `description_category_id` — integer<int64>. Идентификатор категории.
        - `category_name` — string. Название категории.
        - `children` — array[object]. Дерево подкатегорий.
          - `description_category_id` — integer<int64>. Идентификатор категории.
          - `category_name` — string. Название категории.
          - `children` — array[object]. Дерево подкатегорий.
            - `description_category_id` — integer<int64>. Идентификатор категории.
            - `category_name` — string. Название категории.
            - `children` — array[object]. Дерево подкатегорий.
            - `disabled` — boolean. `true`, если в категории нельзя создавать товары. `false`, если можно.
            - `type_id` — integer<int64>. Идентификатор типа товара.
            - `type_name` — string. Название типа товара.
          - `disabled` — boolean. `true`, если в категории нельзя создавать товары. `false`, если можно.
          - `type_id` — integer<int64>. Идентификатор типа товара.
          - `type_name` — string. Название типа товара.
        - `disabled` — boolean. `true`, если в категории нельзя создавать товары. `false`, если можно.
        - `type_id` — integer<int64>. Идентификатор типа товара.
        - `type_name` — string. Название типа товара.
      - `disabled` — boolean. `true`, если в категории нельзя создавать товары. `false`, если можно.
      - `type_id` — integer<int64>. Идентификатор типа товара.
      - `type_name` — string. Название типа товара.
    - `disabled` — boolean. `true`, если в категории нельзя создавать товары. `false`, если можно.
    - `type_id` — integer<int64>. Идентификатор типа товара.
    - `type_name` — string. Название типа товара.
  - `disabled` — boolean. `true`, если в категории нельзя создавать товары. `false`, если можно.
  - `type_id` — integer<int64>. Идентификатор типа товара.
  - `type_name` — string. Название типа товара.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
