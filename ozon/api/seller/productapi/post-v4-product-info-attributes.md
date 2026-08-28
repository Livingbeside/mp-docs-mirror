---
title: Получить описание характеристик товара
api: ozon-seller
method: POST
path: /v4/product/info/attributes
operation_id: ProductAPI_GetProductAttributesV4
tags:
  - ProductAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 599d37d35aeae45a
---

# Получить описание характеристик товара

`POST /v4/product/info/attributes`

Возвращает описание характеристик товаров по идентификатору и видимости. Товар можно искать по `offer_id`, `product_id` или `sku`.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object. Фильтр по товарам.
  - `offer_id` — ?. Фильтр по параметру `offer_id`. Можно передавать список значений.
  - `product_id` — ?. Фильтр по параметру `product_id`. Можно передавать до 1000 значений.
  - `sku` — array[string<int64>]. Идентификатор товара в системе Ozon — SKU.
  - `visibility` — string (ALL, VISIBLE, INVISIBLE, EMPTY_STOCK, NOT_MODERATED, MODERATED, DISABLED, STATE_FAILED, READY_TO_SUPPLY, VALIDATION_STATE_PENDING, VALIDATION_STATE_FAIL, VALIDATION_STATE_SUCCESS…). Фильтр по видимости товара: - `ALL` — все товары, кроме архивных; - `VISIBLE` — товары, которые видны покупателям; - `INVISIBLE` — товары, которые не видны покупателям; - `EMPTY_STOCK` — товары, у которых не указано наличие; - `NOT_MODERATED` — товары, которые не прошли модерацию; - `MODERATED` — товары, которые прошли модерацию; - `DISABLED` — товары, которые видны покупателям, но недоступны к покупке; - `STATE_FAILED` — товары, создание которых завершилось ошибкой; - `READY_TO_SUPPLY` — товары, готовые к поставке; - `VALIDATION_STATE_PENDING` — товары, которые проходят проверку валидатором на премодерации; - `VALIDATION_STATE_FAIL` — товары, которые не прошли проверку валидатором на премодерации; - `VALIDATION_STATE_SUCCESS` — товары, которые прошли проверку валидатором на премодерации; - `TO_SUPPLY` — товары, готовые к продаже; - `IN_SALE` — товары в продаже; - `REMOVED_FROM_SALE` — товары, скрытые от покупателей; - `OVERPRICED` — товары с завышенной ценой; - `CRITICALLY_OVERPRICED` — товары со слишком завышенной ценой; - `EMPTY_BARCODE` — товары без штрихкода; - `BARCODE_EXISTS` — товары со штрихкодом; - `QUARANTINE` — товары на карантине после изменения цены более чем на 50%; - `ARCHIVED` — товары в архиве; - `OVERPRICED_WITH_STOCK` — товары в продаже со стоимостью выше, чем у конкурентов; - `PARTIAL_APPROVED` — товары в продаже с пустым или неполным описанием; - `AUTO_ARCHIVED` — товары, которые система перенесла в архив автоматически; - `MANUAL_ARCHIVED` — товары, которые продавец перенёс в архив вручную; - `SEASONAL_AUTO_ARCHIVED` — сезонные товары, которые система перенесла в архив автоматически; - `VISIBLE_WITH_FBO_STOCK` — товары с остатками на FBO, которые видят покупатели. По умолчанию: `ALL`.
- `last_id` — string. Идентификатор последнего значения на странице. Оставьте это поле пустым при выполнении первого запроса. Чтобы получить следующие значения, укажите `last_id` из ответа предыдущего запроса.
- `limit` — integer<int32>. Количество значений на странице.
- `sort_by` — string. Параметр, по которому товары будут отсортированы: - `sku` — сортировка по идентификатору товара в системе Ozon; - `offer_id` — сортировка по артикулу товара; - `id` — сортировка по идентификатору товара; - `title` — сортировка по названию товара.
- `sort_dir` — string. Направление сортировки: - `asc` — по возрастанию, - `desc` — по убыванию.

## Ответы

**200** — Описание характеристик товара

- `last_id` — string. Идентификатор последнего значения на странице. Чтобы получить следующие значения, укажите полученное значение в следующем запросе в параметре `last_id`.
- `result` — array[object]. Результаты запроса.
  - `attributes` — array[object]. Список характеристик товара.
    - `complex_id` — integer<int64>. Идентификатор характеристики, которая поддерживает вложенные свойства. Например, у характеристики «Процессор» есть вложенные характеристики «Производитель» и «L2 Cache». У каждой из вложенных характеристик может быть несколько вариантов значений.
    - `id` — integer<int64>. Идентификатор характеристики.
    - `values` — array[object]. Массив значений характеристик.
      - `dictionary_value_id` — integer<int64>. Идентификатор характеристики в словаре.
      - `value` — string. Значение характеристики товара.
  - `attributes_with_defaults` — array[integer<int64>]. Список идентификаторов характеристик со значением по умолчанию.
  - `barcode` — string. Штрихкод.
  - `barcodes` — array of strings. Все штрихкоды товара.
  - `color_image` — string. Маркетинговый цвет.
  - `complex_attributes` — array[object]. Массив вложенных характеристик.
    - `complex_id` — integer<int64>. Идентификатор характеристики, которая поддерживает вложенные свойства. Например, у характеристики «Процессор» есть вложенные характеристики «Производитель» и «L2 Cache». У каждой из вложенных характеристик может быть несколько вариантов значений.
    - `id` — integer<int64>. Идентификатор характеристики.
    - `values` — array[object]. Массив значений характеристик.
      - `dictionaryValueId` — integer<int64>. Идентификатор характеристики в словаре.
      - `value` — string. Значение характеристики товара.
  - `depth` — integer<int64>. Глубина.
  - `description_category_id` — integer<int64>. Идентификатор категории. Используйте его с методами [/v1/description-category/attribute](#operation/DescriptionCategoryAPI_GetAttributes) и [/v1/description-category/attribute/values](#operation/DescriptionCategoryAPI_GetAttributeValues).
  - `dimension_unit` — string. Единица измерения габаритов: - `mm` — миллиметры, - `cm` — сантиметры, - `in` — дюймы.
  - `height` — integer<int64>. Высота упаковки.
  - `id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `images` — array of strings. Массив ссылок на изображения товара. Порядок изображений аналогичен порядку в карточке товаров.
    - `default` — boolean. `true`, если изображение главное и отображается первым на карточке товара.
    - `file_name` — string
    - `index` — integer<int64>
  - `model_info` — object. Информация о модели.
    - `count` — integer<int64>. Количество объединённых товаров модели.
    - `model_id` — integer<int64>. Идентификатор модели.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `pdf_list` — array[object]. Массив PDF-файлов.
    - `file_name` — string. Путь к PDF-файлу.
    - `name` — string. Название файла.
  - `primary_image` — string. Ссылка на главное изображение товара.
  - `sku` — string. Идентификатор товара в системе Ozon — SKU.
  - `type_id` — integer<int64>. Идентификатор типа товара.
  - `weight` — integer<int64>. Вес товара в упаковке.
  - `weight_unit` — string. Единица измерения веса.
  - `width` — integer<int64>. Ширина упаковки.
- `total` — string<int64>. Количество товаров в списке.

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
