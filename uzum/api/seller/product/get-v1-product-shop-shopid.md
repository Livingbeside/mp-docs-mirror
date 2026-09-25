---
title: Получение SKU по ID магазина
api: uzum-seller
method: GET
path: /v1/product/shop/{shopId}
operation_id: getShopProductsByShopId
tags:
  - Product
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 88b1568084b2b8b7
---

# Получение SKU по ID магазина

`GET /v1/product/shop/{shopId}`

Этот метод позволяет получить список товаров и остатков, доступных в указанном магазине.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `searchQuery` | query | string | нет | Запрос для поиска товаров по названию или описанию. |
| `sortBy` | query | string (DEFAULT, ORDERS, PRICE, ID, ROI, CONVERSION, LEFTOVERS, CREATED_AND_TITLE) | нет | Критерий сортировки товаров. Доступные варианты: DEFAULT, ORDERS, PRICE, ID, ROI, CONVERSION, LEFTOVERS, CREATED_AND_TITLE. |
| `order` | query | string (ASC, DESC) | нет | Направление сортировки: ASC (по возрастанию) или DESC (по убыванию). |
| `size` | query | integer<int32> | да | Количество товаров, возвращаемых в одном запросе. |
| `page` | query | integer<int32> | да | Номер страницы для постраничного просмотра товаров. |
| `shopId` | path | integer<int64> | да | ID магазина, для которого необходимо получить товары. |
| `productRank` | query | string (A, B, C, N, D) | нет | Категория товара, которую нужно отобразить. Возможные значения: A, B, C, N, D. |
| `filter` | query | string (ALL, ACTIVE, INACTIVE, WARNING, WITH_SKU, ARCHIVE, DEFECTED, WITHOUT_REQUIRED_FILTERS) | нет | Фильтр для отображения товаров. Доступные значения: ALL, ACTIVE, INACTIVE, WARNING, WITH_SKU, ARCHIVE, DEFECTED, WITHOUT_REQUIRED_FILTERS. |

## Ответы

**200** — OK

- `productList` — array[object]. Список всех продуктов, доступных в магазине.
  - `productId` — integer<int64>. Уникальный идентификатор продукта.
  - `category` — string. Категория, к которой принадлежит продукт.
  - `rating` — string. Рейтинг продукта, выраженный числом или символом.
  - `status` — object. Статус продукта, показывающий текущее состояние товара.
    - `id` — integer<int32>. Уникальный идентификатор статуса продукта.
    - `title` — string. Название статуса продукта, например, 'Готов к отправке'.
    - `value` — string (NO_SKU, IN_STOCK, READY_TO_SEND, SENT, RUN_OUT, BLOCKED, SKU_BLOCKED, ARCHIVED, DELETED, PERM_BANNED, NOT_READY_TO_SEND). Значение статуса, указывающее текущее состояние продукта.
    - `description` — string. Описание статуса, объясняющее его значение для продавца.
    - `color` — string. Цвет, ассоциированный с данным статусом для визуальной индикации.
    - `additional` — array[object]. Дополнительные статусы продукта, например, временные состояния.
      - `id` — integer<int32>. Уникальный идентификатор дополнительного статуса продукта.
      - `title` — string. Название дополнительного статуса.
      - `description` — string. Описание дополнительного статуса, объясняющее его значение.
      - `color` — string. Цвет, ассоциированный с дополнительным статусом, для визуальной индикации.
      - `icon` — string. Иконка, отображаемая для дополнительного статуса.
  - `moderationStatus` — object. Статус модерации, указывающий, прошел ли продукт проверку.
    - `title` — string. Название статуса модерации, например, 'На модерации'.
    - `color` — string. Цвет, связанный со статусом модерации, для визуального отображения.
    - `value` — string (NOT_MODERATED, MODERATED, ON_MODERATION, HAS_COMPLAINTS, ON_PREMODERATION, PERM_BANNED). Значение статуса модерации, показывающее текущий этап модерации продукта.
    - `hasAnySkuBlocked` — boolean. Показывает, был ли заблокирован какой-либо SKU из данного продукта.
  - `commission` — number<double>. Процент комиссии за продажу продукта. Возможно устарело и заменено на 'commissionDto'.
  - `commissionDto` — object. Детали комиссии, взимаемой за продукт, включая минимальную и максимальную ставку.
    - `minCommission` — number<double>. Минимальная ставка комиссии, взимаемая с продавца за продажу продукта.
    - `maxCommission` — number<double>. Максимальная ставка комиссии, взимаемая с продавца за продажу продукта.
  - `skuList` — array[object]. Список SKU, связанных с продуктом.
    - `skuTitle` — string. Название SKU (единицы хранения) товара.
    - `skuFullTitle` — string. Полное название SKU товара, включающее все детали.
    - `productTitle` — string. Название продукта, к которому относится SKU.
    - `skuId` — integer<int64>. Уникальный идентификатор SKU товара.
    - `quantityCreated` — integer<int32>. Общее количество созданных единиц SKU.
    - `quantityActive` — integer<int32>. Количество активных единиц SKU на складе.
    - `quantityFbs` — integer<int32>. Количество единиц SKU, доступных в режиме FBS (Fulfillment by Seller).
    - `quantityAdditional` — integer<int32>. Дополнительное количество SKU, которое может быть задействовано при необходимости.
    - `quantityOnPhotoStudio` — integer<int32>. Количество SKU, находящихся в фотостудии для съемки.
    - `quantityArchived` — integer<int32>. Количество архивированных SKU.
    - `quantitySold` — integer<int32>. Общее количество проданных SKU.
    - `quantityReturned` — integer<int32>. Количество возвращенных покупателем SKU.
    - `quantityMissing` — integer<int32>. Количество недостающих SKU (параметр устарел).
    - `quantityDefected` — integer<int32>. Количество дефектных SKU.
    - `quantityPending` — integer<int32>. Количество SKU в ожидании обработки или отправки.
    - `returnedPercentage` — number<double>. Процент возвращенных SKU относительно общего количества проданных.
    - `barcode` — integer<int64>. Штрих-код SKU для идентификации.
    - `archived` — boolean. Показывает, находится ли SKU в архиве.
    - `commission` — number<double>. Комиссия, связанная с продажей данного SKU.
    - `characteristics` — string. Описание характеристик SKU, может включать основные атрибуты.
    - `purchasePrice` — integer<int64>. Цена закупки данного SKU.
    - `price` — integer<int64>. Цена продажи SKU.
    - `blockingReason` — string. Причина блокировки SKU, если оно заблокировано.
    - `skuBlockReason` — object. Детали причины блокировки SKU, если оно заблокировано.
      - `title` — string. Название причины блокировки SKU.
      - `message` — string. Сообщение с деталями причины блокировки.
      - `date` — string<date-time>. Дата, когда SKU был заблокирован.
    - `blocked` — boolean. Показывает, заблокировано ли SKU.
    - `rankInfo` — object. Информация о ранге продукта, включая его позицию на рынке.
      - `rank` — string (A, B, C, N, D). Ранг продукта, представляющий его классификацию по уровню популярности или качества.
      - `rankValue` — string. Числовое значение ранга, характеризующее позицию продукта.
      - `dateUpdated` — string<date-time>. Дата последнего обновления информации о ранге.
    - `article` — string. Артикул SKU, используемый для идентификации продукта продавцом.
    - `turnover` — number<double>. Оборот по данному SKU в денежном выражении.
    - `dimensionalGroup` — string. Габаритная группа SKU, указывающая его размер или вес.
    - `paidStorageDimensionalGroup` — object. Габаритная группа для оплачиваемого хранения SKU.
      - `group` — string (SMALL, MEDIUM, LARGE, UNKNOWN). Категория размера товара, например, малая, средняя или большая.
      - `title` — string. Название категории размера.
    - `paidStoragePriceItem` — integer<int64>. Стоимость единицы хранения для SKU в оплачиваемом режиме.
    - `paidStorageAmount` — integer<int64>. Общая стоимость хранения SKU в оплачиваемом режиме.
    - `actualDimensionalGroup` — object. Фактическая габаритная группа SKU.
      - `group` — string (SMALL, MEDIUM, LARGE, UNKNOWN). Категория размера товара, например, малая, средняя или большая.
      - `title` — string. Название категории размера.
    - `hasStudioPhoto` — boolean. Показывает, есть ли у SKU студийное фото.
    - `avgdsales` — number<double>. Среднее количество продаж данного SKU в день.
    - `avgdquantity` — number<double>. Среднее количество активных единиц SKU в день.
    - `pstorage` — boolean. Показывает, находится ли SKU на платном складе хранения.
    - `previewImage` — string. Ссылка на фото превью товара
    - `ikpu` — string. Идентификационный код продукции и услуг для Узбекистана, представлен в виде набора символов (чисел)
    - `sellerItemCode` — string. Идентификатор селлера
  - `skuTitle` — string. Название SKU продукта.
  - `image` — string. URL изображения продукта.
  - `previewImg` — string. URL предпросмотра изображения продукта.
  - `title` — string. Название продукта.
  - `quantityActive` — integer<int32>. Количество активных единиц продукта на складе.
  - `quantityFbs` — integer<int32>. Количество единиц, доступных в режиме FBS (Fulfillment by Seller).
- `totalProductsAmount` — integer<int32>. Общее количество доступных продуктов.
