---
title: Получить доступные варианты доставки
api: ozon-seller
method: POST
path: /v2/delivery/checkout
operation_id: DeliveryCheckout
tags:
  - DeliveryAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: bdba3b41a5229a5e
---

# Получить доступные варианты доставки

`POST /v2/delivery/checkout`

Проверяет доступность доставки товаров на указанный адрес или в точку выдачи и отображает сроки доставки.

Проверяйте наличие товаров и маршруты во время оформления заказа, чтобы точно рассчитать сроки доставки.

## Запрос

**Тело запроса** (`application/json`):

- `buyer_phone` — string. Номер телефона покупателя.
- `delivery_schema` — string (MIX, FBO, FBS). Схема доставки: - `MIX` — на выбор Ozon; - `FBO` — FBO; - `FBS` — FBS. По умолчанию: `MIX`.
- `delivery_type` — object. Способ доставки.
  - `courier` — object. Доставка курьером.
    - `coordinates` — object. Координаты точки доставки.
      - `latitude` — number<double>. Широта.
      - `longitude` — number<double>. Долгота.
  - `pick_up` — object. Самовывоз.
    - `map_point_id` — integer<int64>. Идентификатор пункта самовывоза.
- `items` — array[object]. Информация о товарах.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `quantity` — integer<int64>. Количество товара.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

## Ответы

**200** — Успешно

- `splits` — array[object]. Результат запроса.
  - `commissions` — object. Информация о комиссиях за доставку отправления. Если `commissions = null`, вариант доставки недоступен.
    - `total` — object. Стоимость доставки отправления из заказа с учётом комиссии.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
  - `delivery_method` — object. Метод доставки.
    - `delivery_time_zone_offset` — integer<int64>. Смещение часового пояса доставки в минутах.
    - `delivery_type` — string (UNSPECIFIED, POSTAMAT, COURIER, PVZ). Способ доставки: - `UNSPECIFIED` — не определён; - `POSTAMAT` — в постамат; - `COURIER` — курьером; - `PVZ` — в пункт самовывоза. По умолчанию: `UNSPECIFIED`.
    - `id` — integer<int64>. Идентификатор метода доставки.
    - `name` — string. Название метода доставки.
    - `timeslots` — array[object]. Таймслоты.
      - `client_date_range` — object. Интервал времени, когда покупатель может получить заказ.
        - `from` — string<date-time>. Дата и время начала интервала.
        - `to` — string<date-time>. Дата и время конца интервала.
      - `logistic_date_range` — object. Интервал времени, в течение которого заказ может быть доставлен до пункта выдачи.
        - `from` — string<date-time>. Дата и время начала интервала.
        - `to` — string<date-time>. Дата и время конца интервала.
      - `timeslot_id` — integer<int64>. Идентификатор таймслота.
    - `unavailable_reason` — string (UNSPECIFIED, UNKNOWN, OUT_OF_STOCK, BANNED_FOR_AREA, BANNED_FOR_LEGAL, BANNED, BANNED_FOR_NOT_PREMIUM, DELIVERY_UNAVAILABLE, BANNED_FOR_INDIVIDUAL, INVALID_WEIGHT, INVALID_MULTIPLICITY, NOT_FOUND_POINTS_DARK_STORES…). Причина недоступности: - `UNSPECIFIED` — доставка доступна; - `UNKNOWN` — неизвестная причина; - `OUT_OF_STOCK` — товар закончился; - `BANNED_FOR_AREA` — товар заблокирован для этой области; - `BANNED_FOR_LEGAL` — товар заблокирован для юридических лиц; - `BANNED` — товар заблокирован; - `BANNED_FOR_NOT_PREMIUM` — товар заблокирован для покупателей без подписки Premium; - `DELIVERY_UNAVAILABLE` — доставка недоступна, например, курьеры перегружены; - `BANNED_FOR_INDIVIDUAL` — товар заблокирован для физических лиц; - `INVALID_WEIGHT` — вес товара не указан; - `INVALID_MULTIPLICITY` — недопустимая кратность в штуках; - `NOT_FOUND_POINTS_DARK_STORES` — пункты в массиве дарксторов не найдены; - `INVALID_MULTI_WAREHOUSES` — товары в заказе с разными схемами доставки неверно распределены; - `MIN_PRICE` — сплит не прошёл минимальную цену; - `OZONE_DELIVERY_UNAVAILABLE` — доставка Ozon недоступна; - `RFBS_DELIVERY_UNAVAILABLE` — доставка по системе rFBS недоступна; - `HACK_COURIER_TAGS` — способ доставки исключён по правилу приоритетного показа; - `NO_SLA` — норматив комплектации отсутствует; - `DELIVERY_VARIANT_IS_CLOSING` — способ доставки в неподходящем статусе; - `TPL_NOT_INTEGRATED` — точки, по которым возврат невозможен; - `NOT_ALL_WAREHOUSES_ARE_SERVED` — доставка со склада отправления отсутствует; - `DELIVERY_SLOTS_NOT_FOUND` — таймслоты отсутствуют; - `NO_ROUTE` — маршрут не найден; - `CAPACITY_LIMIT` — таймслоты отсеяны из-за заполненности капаситета; - `PACKAGE_MAX_VOLUME_WEIGHT_RESTRICTION` — ограничение на максимальный объёмный вес посылки; - `PACKAGE_MAX_WEIGHT_RESTRICTION` — ограничение на максимальный физический вес посылки, в килограммах до тысячных грамма; - `MAX_COST_RESTRICTION` — ограничение на максимальную стоимость заказа, учитывается стоимость товаров, их доставки, но не учитывается страховой сбор в рублях; - `MIN_PACKAGE_WEIGHT_RESTRICTION` — ограничение на минимальный физический вес посылки в килограммах до тысячных грамма; - `MIN_COST_RESTRICTION` — ограничение на минимальную стоимость товаров заказа в рублях; - `MAX_DIMENSIONS_RESTRICTION` — ограничение на максимальные габариты посылки в сантиметрах; - `PRODUCT_TYPES_RESTRICTION` — ограничение на допустимые в заказе товарные категории; - `PRODUCT_TAGS_RESTRICTION` — ограничение на допустимые в заказе теги товаров; - `SELECTED_DELIVERY_METHOD_UNAVAILABLE` — выбранный способ доставки стал недоступным; - `SELECTED_DELIVERY_TIMESLOT_UNAVAILABLE` — выбранный таймслот стал недоступным; - `MARKETPLACE_UNAVAILABLE` — в заказе товары нескольких маркетплейсов, оформить заказ можно только с 1; - `INVALID_PVZ_FOR_KGT` — выбранный ПВЗ не подходит для КГТ; - `LEGAL_USER_PREMIUM_SPLIT` — юридическим лицам запрещена покупка подписки Premium; - `USER_ALREADY_HAS_PREMIUM` — у пользователя уже есть подписка Premium и она не подарочная; - `WAIT_FOR_PAY_SUBSCRIPTION` — пользователь купил премиум-подписку, но не оплатил заказ или подписка ещё не перешла в активный статус; - `ADDRESS_NOT_SET ` — адрес не установлен; - `PICKUP_POINT_DISABLED` — ПВЗ недоступен; - `LEGAL_PREORDER` — предзаказ недоступен юридическим лицам; - `DELIVERY_TYPE_FOR_PREORDER` — тип доставки недоступен для предзаказа; - `CROSS_BORDER_PICKUP` — CrossBorder-товары не доставляются в пункты выдачи; - `ORDER_CUSTOMS_TYPES` — ограничения на таможенные типы; - `PACKAGE_MAX_COST` — ограничение на максимальную стоимость посылки,учитывается стоимость товаров и их доставки; - `SUPER_ECONOM` — недоступный «суперэконом»; - `ECONOM_NOT_FULL_QUANT` — неполный квант; - `EMPTY_DELIVERY_METHODS` — нет доступных способов доставки; По умолчанию: `UNSPECIFIED`.
    - `warehouse_time_zone_offset` — integer<int64>. Смещение часового пояса склада в минутах.
  - `delivery_schema` — string (UNSPECIFIED, FBO, FBS). Схема доставки: - `UNSPECIFIED` — не определена; - `FBO` — FBO; - `FBS` — FBS. По умолчанию: `UNSPECIFIED`.
  - `items` — array[object]. Информация о товарах.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `quantity` — integer<int64>. Количество товара.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `unavailable_reason` — string (UNSPECIFIED, UNKNOWN, OUT_OF_STOCK, BANNED_FOR_AREA, BANNED_FOR_LEGAL, BANNED, BANNED_FOR_NOT_PREMIUM, DELIVERY_UNAVAILABLE, BANNED_FOR_INDIVIDUAL, INVALID_WEIGHT, INVALID_MULTIPLICITY, NOT_FOUND_POINTS_DARK_STORES…). Причина недоступности: - `UNSPECIFIED` — доставка доступна; - `UNKNOWN` — неизвестная причина; - `OUT_OF_STOCK` — товар закончился; - `BANNED_FOR_AREA` — товар заблокирован для этой области; - `BANNED_FOR_LEGAL` — товар заблокирован для юридических лиц; - `BANNED` — товар заблокирован; - `BANNED_FOR_NOT_PREMIUM` — товар заблокирован для покупателей без подписки Premium; - `DELIVERY_UNAVAILABLE` — доставка недоступна, например, курьеры перегружены; - `BANNED_FOR_INDIVIDUAL` — товар заблокирован для физических лиц; - `INVALID_WEIGHT` — вес товара не указан; - `INVALID_MULTIPLICITY` — недопустимая кратность в штуках; - `NOT_FOUND_POINTS_DARK_STORES` — пункты в массиве дарксторов не найдены; - `INVALID_MULTI_WAREHOUSES` — товары в заказе с разными схемами доставки неверно распределены; - `MIN_PRICE` — сплит не прошёл минимальную цену; - `OZONE_DELIVERY_UNAVAILABLE` — доставка Ozon недоступна; - `RFBS_DELIVERY_UNAVAILABLE` — доставка по системе rFBS недоступна; - `HACK_COURIER_TAGS` — способ доставки исключён по правилу приоритетного показа; - `NO_SLA` — норматив комплектации отсутствует; - `DELIVERY_VARIANT_IS_CLOSING` — способ доставки в неподходящем статусе; - `TPL_NOT_INTEGRATED` — точки, по которым возврат невозможен; - `NOT_ALL_WAREHOUSES_ARE_SERVED` — доставка со склада отправления отсутствует; - `DELIVERY_SLOTS_NOT_FOUND` — таймслоты отсутствуют; - `NO_ROUTE` — маршрут не найден; - `CAPACITY_LIMIT` — таймслоты отсеяны из-за заполненности капаситета; - `PACKAGE_MAX_VOLUME_WEIGHT_RESTRICTION` — ограничение на максимальный объёмный вес посылки; - `PACKAGE_MAX_WEIGHT_RESTRICTION` — ограничение на максимальный физический вес посылки, в килограммах до тысячных грамма; - `MAX_COST_RESTRICTION` — ограничение на максимальную стоимость заказа, учитывается стоимость товаров, их доставки, но не учитывается страховой сбор в рублях; - `MIN_PACKAGE_WEIGHT_RESTRICTION` — ограничение на минимальный физический вес посылки в килограммах до тысячных грамма; - `MIN_COST_RESTRICTION` — ограничение на минимальную стоимость товаров заказа в рублях; - `MAX_DIMENSIONS_RESTRICTION` — ограничение на максимальные габариты посылки в сантиметрах; - `PRODUCT_TYPES_RESTRICTION` — ограничение на допустимые в заказе товарные категории; - `PRODUCT_TAGS_RESTRICTION` — ограничение на допустимые в заказе теги товаров; - `SELECTED_DELIVERY_METHOD_UNAVAILABLE` — выбранный способ доставки стал недоступным; - `SELECTED_DELIVERY_TIMESLOT_UNAVAILABLE` — выбранный таймслот стал недоступным; - `MARKETPLACE_UNAVAILABLE` — в заказе товары нескольких маркетплейсов, оформить заказ можно только с 1; - `INVALID_PVZ_FOR_KGT` — выбранный ПВЗ не подходит для КГТ; - `LEGAL_USER_PREMIUM_SPLIT` — юридическим лицам запрещена покупка подписки Premium; - `USER_ALREADY_HAS_PREMIUM` — у пользователя уже есть подписка Premium и она не подарочная; - `WAIT_FOR_PAY_SUBSCRIPTION` — пользователь купил премиум-подписку, но не оплатил заказ или подписка ещё не перешла в активный статус; - `ADDRESS_NOT_SET ` — адрес не установлен; - `PICKUP_POINT_DISABLED` — ПВЗ недоступен; - `LEGAL_PREORDER` — предзаказ недоступен юридическим лицам; - `DELIVERY_TYPE_FOR_PREORDER` — тип доставки недоступен для предзаказа; - `CROSS_BORDER_PICKUP` — CrossBorder-товары не доставляются в пункты выдачи; - `ORDER_CUSTOMS_TYPES` — ограничения на таможенные типы; - `PACKAGE_MAX_COST` — ограничение на максимальную стоимость посылки,учитывается стоимость товаров и их доставки; - `SUPER_ECONOM` — недоступный «суперэконом»; - `ECONOM_NOT_FULL_QUANT` — неполный квант; - `EMPTY_DELIVERY_METHODS` — нет доступных способов доставки; По умолчанию: `UNSPECIFIED`.
  - `warehouse_id` — integer<int64>. Идентификатор склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `@type` — string. Тип протокола передачи данных.
  - `code` — string. Идентификатор ошибки: `USER_DELIVERY_UNAVAILABLE` — нельзя доставить товары этому покупателю.
  - `message` — string. Описание ошибки.
- `message` — string. Описание ошибки.
