---
title: Получить информацию о грузоместах
api: ozon-seller
method: POST
path: /v1/carriage/container/get
operation_id: CarriageContainerGet
tags:
  - CarriageAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 43949f7aebb59b9d
---

# Получить информацию о грузоместах

`POST /v1/carriage/container/get`

Вы можете оставить обратную связь по этому методу в комментариях к обсуждению в [сообществе разработчиков Ozon for dev](https://dev.ozon.ru/community/2059-Beta-metody-dlia-raboty-s-doveritelnoi-priemkoi/).

## Запрос

**Тело запроса** (`application/json`):

- `container_id` — integer<int64> **обязательный**. Идентификатор грузоместа.

## Ответы

**200** — Информация о грузоместах

- `available_actions` — array[string]. Действия с грузоместом: - `approve` — подтвердить состав; - `get_label_container` — получить этикетку; - `delete` — удалить; - `place_box_into_pallet` — добавить коробку на палету; - `remove_box_from_pallet` — убрать коробку с палеты; - `place_posting_into_container` — перенести отправление в другое грузоместо; - `remove_posting_from_container` — убрать отправление из грузоместа; - `get_documents` — получить транспортную накладную.
- `cargo_type` — string. Тип грузоместа.
- `container_id` — integer<int64>. Идентификатор грузоместа.
- `container_number` — integer<int32>. Порядковый номер грузоместа.
- `count_of_postings` — integer<int32>. Количество отправлений в грузоместе.
- `created_at` — string<date-time>. Дата создания грузоместа в UTC.
- `parent_container_id` — integer<int64>. Идентификатор родительского грузоместа.
- `postings` — array[object]. Список отправлений.
  - `available_actions` — array[string]. Действия с отправлением.
  - `in_process_at` — string<date-time>. Дата и время начала обработки отправления.
  - `posting_number` — string. Номер отправления.
  - `products` — array[object]. Список товаров.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `quantity` — integer<int32>. Количество экземпляров.
    - `picture_url` — string. Ссылка на изображение товара.
    - `product_color` — string. Цвет товара.
    - `product_size_manufacturer` — string. Размер производителя.
    - `product_size_russian` — string. Российский размер.
  - `sort_type` — string. Тип сортировки грузоместа: - `sort` — сортируемый; - `non-sort` — несортируемый.
  - `weight` — number<float>. Вес отправления, кг.
- `related_container_ids` — array[string<int64>]. Идентификаторы дочерних грузомест.
- `sort_type` — string. Тип сортировки грузоместа: - `sort` — сортируемый; - `non-sort` — несортируемый.
- `status` — string. Статус грузоместа.
- `warehouse_date` — string. Дата создания грузоместа в часовом поясе склада.
- `warehouse_id` — integer<int64>. Идентификатор склада продавца.
- `warehouse_name` — string. Название склада.
- `weight` — number<float>. Суммарный вес отправлений в грузоместе, кг.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
