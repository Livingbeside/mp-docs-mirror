---
title: Получить информацию о товарах по идентификаторам
api: ozon-seller
method: POST
path: /v3/product/info/list
operation_id: ProductAPI_GetProductInfoList
tags:
  - ProductAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 833998e31743c35e
---

# Получить информацию о товарах по идентификаторам

`POST /v3/product/info/list`

Метод для получения информации о товарах по их идентификаторам.

В теле запроса должен быть массив однотипных идентификаторов, в ответе будет массив `items`.

В одном запросе вы можете передать не больше 1000 товаров по параметрам `offer_id`, `product_id` и `sku` в сумме.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `offer_id` — array[string]. Идентификатор товара в системе продавца — артикул.
- `product_id` — array[string<int64>]. Идентификатор товара в системе Ozon — `product_id`.
- `sku` — array[string<int64>]. Идентификатор товара в системе Ozon — SKU.

## Ответы

**200** — Список товаров

- `items` — array[object]. Массив данных.
  - `availabilities` — array[object]. Информация о доступности товара.
    - `availability` — string (HIDDEN, AVAILABLE, UNAVAILABLE). Доступность товара: - `HIDDEN` — скрыт; - `AVAILABLE` — доступен; - `UNAVAILABLE` — недоступен, SKU удалён.
    - `reasons` — array[object]. Причина, почему товар скрыт.
      - `human_text` — object. Информация о причине.
        - `text` — string. Описание причины.
      - `id` — integer<int64>. Идентификатор причины.
    - `sku` — integer<int64>. Идентификатор товара.
    - `source` — string. Ссылка на источник.
  - `barcodes` — array[string]. Все штрихкоды товара.
  - `color_image` — array[string]. Изображение цвета товара.
  - `commissions` — array[object]. Информация о комиссиях.
    - `delivery_amount` — number<double>. Стоимость доставки.
    - `percent` — number<double>. Процент комиссии.
    - `return_amount` — number<double>. Стоимость возврата.
    - `sale_schema` — string. Схема продажи.
    - `value` — number<double>. Сумма комиссии.
  - `created_at` — string<date-time>. Дата и время создания товара.
  - `currency_code` — string. Валюта.
  - `description_category_id` — integer<int64>. Идентификатор категории. Используйте его с методами [/v1/description-category/attribute](#operation/DescriptionCategoryAPI_GetAttributes) и [/v1/description-category/attribute/values](#operation/DescriptionCategoryAPI_GetAttributeValues).
  - `discounted_fbo_stocks` — integer<int32>. Остатки уценённого товара на складе Ozon.
  - `errors` — array[object]. Информация об ошибках при создании или валидации товара.
    - `attribute_id` — integer<int64>. Идентификатор характеристики.
    - `code` — string. Код ошибки.
    - `field` — string. Поле, в котором найдена ошибка.
    - `level` — string (ERROR_LEVEL_UNSPECIFIED, ERROR_LEVEL_ERROR, ERROR_LEVEL_WARNING, ERROR_LEVEL_INTERNAL). Описание уровней ошибок: - `ERROR_LEVEL_UNSPECIFIED` — не определён; - `ERROR_LEVEL_ERROR` — критичная ошибка, товар нельзя продавать; - `ERROR_LEVEL_INTERNAL` — критичная ошибка, товар нельзя продавать. - `ERROR_LEVEL_WARNING` — некритичная ошибка, товар можно продавать. [Подробнее об ошибках при создании товара в Базе знаний продавца](https://seller-edu.ozon.ru/work-with-goods/zagruzka-tovarov/creating-goods/oshibki-pri-rabote-s-kartochkami) По умолчанию: `ERROR_LEVEL_UNSPECIFIED`.
    - `state` — string. Статус товара, в котором произошла ошибка.
    - `texts` — object. Описание ошибок.
      - `attribute_name` — string. Название атрибута, в котором произошла ошибка.
      - `description` — string. Описание ошибки.
      - `hint_code` — string. Код ошибки в системе Ozon.
      - `message` — string. Текст ошибки.
      - `params` — array[object]. В каких параметрах допущена ошибка.
        - `name` — string. Название параметра.
        - `value` — string. Значение параметра.
      - `short_description` — string. Краткое описание ошибки.
  - `has_discounted_fbo_item` — boolean. Признак, что у товара есть уценённые аналоги на складе Ozon.
  - `id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `images` — array[string]. Массив ссылок на изображения. Изображения в массиве расположены в порядке их расположения на сайте. Если параметр `primary_image` не указан, первое изображение в массиве главное для товара.
  - `is_archived` — boolean. `true`, если товар архивирован вручную.
  - `is_autoarchived` — boolean. `true`, если товар архивирован автоматически.
  - `is_discounted` — boolean. Признак, является ли товар уценённым: - Если товар создавался продавцом как уценённый — `true`. - Если товар не уценённый или был уценён Ozon — `false`.
  - `is_kgt` — boolean. `true`, если товар крупногабаритный. Только для схемы FBS.
  - `is_prepayment_allowed` — boolean. `true`, если возможна предоплата.
  - `is_super` — boolean. Признак супер-товара. [Подробнее о супер-товарах в Базе знаний продавца](https://seller-edu.ozon.ru/fbo/rabota-so-stokom/super-tovary)
  - `min_price` — string. Минимальная цена товара после применения акций.
  - `model_info` — object. Информация о модели товара.
    - `count` — integer<int64>. Количество товаров в ответе.
    - `model_id` — integer<int64>. Идентификатор модели товара.
  - `name` — string. Название.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `old_price` — string. Цена до учёта скидок. На карточке товара отображается зачёркнутой.
  - `price` — string. Цена товара с учётом скидок — это значение показывается на карточке товара.
  - `price_indexes` — object. Ценовые индексы товара.
    - `color_index` — string (COLOR_INDEX_UNSPECIFIED, COLOR_INDEX_WITHOUT_INDEX, COLOR_INDEX_SUPER, COLOR_INDEX_GREEN, COLOR_INDEX_YELLOW, COLOR_INDEX_RED). Виды индекса цен: - `COLOR_INDEX_UNSPECIFIED` — не определён, - `COLOR_INDEX_WITHOUT_INDEX` — отсутствует, - `COLOR_INDEX_SUPER` — супервыгодный, - `COLOR_INDEX_GREEN` — выгодный, - `COLOR_INDEX_YELLOW` — умеренный, - `COLOR_INDEX_RED` — невыгодный. [Подробнее об индексе цен в Базе знаний продавца](https://seller-edu.ozon.ru/ceny-i-akcii/rabota-s-cenami/price-index) По умолчанию: `COLOR_INDEX_UNSPECIFIED`.
    - `external_index_data` — object. Цена товара у конкурентов на других площадках.
      - `minimal_price` — string. Минимальная цена товара у конкурентов на другой площадке.
      - `minimal_price_currency` — string. Валюта цены.
      - `price_index_value` — number<double>. Значение индекса цены.
    - `ozon_index_data` — object. Цена товара у конкурентов на Ozon.
      - `minimal_price` — string. Минимальная цена товара у конкурентов на Ozon.
      - `minimal_price_currency` — string. Валюта цены.
      - `price_index_value` — number<double>. Значение индекса цены.
    - `self_marketplaces_index_data` — object. Цена вашего товара на других площадках.
      - `minimal_price` — string. Минимальная цена вашего товара на других площадках.
      - `minimal_price_currency` — string. Валюта цены.
      - `price_index_value` — number<double>. Значение индекса цены.
  - `primary_image` — array[string]. Главное изображение товара.
  - `promotions` — array[object]. Акции.
    - `is_enabled` — boolean. `true`, если акция включена.
    - `type` — string (UNSPECIFIED, REVIEWS_PROMO). Тип акции: - `UNSPECIFIED` — не определено; - `REVIEWS_PROMO` — акция «Ускоренный сбор отзывов». По умолчанию: `UNSPECIFIED`.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `sources` — array[object]. Информация об источниках создания товара. С 1 июля 2023 года продавцы создают товары по схеме SDS.
    - `created_at` — string<date-time>. Дата создания товара.
    - `quant_code` — string. Список квантов с товарами.
    - `shipment_type` — string (SHIPMENT_TYPE_UNSPECIFIED, SHIPMENT_TYPE_GENERAL, SHIPMENT_TYPE_BOX, SHIPMENT_TYPE_PALLET). Тип упаковки: - `SHIPMENT_TYPE_UNSPECIFIED` — не указано; - `SHIPMENT_TYPE_GENERAL` — обычный товар; - `SHIPMENT_TYPE_BOX` — коробка; - `SHIPMENT_TYPE_PALLET` — палета. По умолчанию: `SHIPMENT_TYPE_UNSPECIFIED`.
    - `sku` — integer<int64>. Идентификатор товара на Ozon — SKU.
    - `source` — string. Схема продажи: - `SDS` — FBO и FBS с одинаковым SKU; - `FBO`; - `FBS`.
  - `statuses` — object. Информация о статусах товара.
    - `is_created` — boolean. `true`, если товар создан корректно.
    - `moderate_status` — string. Статус модерации.
    - `status` — string. Статус товара.
    - `status_description` — string. Описание статуса товара.
    - `status_failed` — string. Статус товара, в котором возникла ошибка.
    - `status_name` — string. Название статуса товара.
    - `status_tooltip` — string. Описание статуса.
    - `status_updated_at` — string<date-time>. Время последнего изменения статуса.
    - `validation_status` — string. Статус валидации.
  - `stocks` — object. Информация об остатках товара.
    - `has_stock` — boolean. `true`, если есть остаток на складах.
    - `stocks` — array[object]. Статус остатков товара.
      - `present` — integer<int32>. Сейчас на складе.
      - `reserved` — integer<int32>. Зарезервировано.
      - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
      - `source` — string. Схема продажи.
  - `type_id` — integer<int64>. Идентификатор типа товара.
  - `updated_at` — string<date-time>. Дата последнего обновления товара.
  - `vat` — string. Ставка НДС для товара.
  - `visibility_details` — object. Настройки видимости товара.
    - `has_price` — boolean. Если установлена цена — `true`.
    - `has_stock` — boolean. Если есть остаток на складах — `true`.
  - `volume_weight` — number<double>. Объёмный вес товара.

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
