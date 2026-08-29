---
title: Получить список отправлений
api: ozon-seller
method: POST
path: /v4/posting/fbs/list
operation_id: PostingFbsList
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 21d3d2832193fae6
---

# Получить список отправлений

`POST /v4/posting/fbs/list`

Возвращает список отправлений за указанный период времени — он должен быть не больше одного года.

 Чтобы получать актуальную дату отгрузки, регулярно обновляйте информацию об отправлениях или подключите [пуш-уведомления](#tag/push_start).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object **обязательный**. Фильтр.
  - `delivery_method_ids` — array[string<int64>]. Идентификатор способа доставки. Можно получить с помощью метода [/v1/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodList).
  - `integration_type_flow` — array[string]. Процесс обработки отправления: - `ozon` — доставка силами Ozon; - `aggregator` — доставка внешней службой, Ozon регистрирует заказ; - `non_integrated` — доставка силами продавца; - `3pl_tracking` — доставка внешней службой, продавец регистрирует заказ; - `hybrid` — гибридная интеграция; - `hybrid_aggregator` — гибридная интеграция с доставкой внешней службой, Ozon регистрирует заказ; - `hybrid_non_integrated` — гибридная интеграция с доставкой силами продавца; - `hybrid_3pl_tracking` — гибридная интеграция с доставкой внешней службой, продавец регистрирует заказ; - `click_and_collect` — бронирование в магазине партнёра; - `FBP` — доставка с партнёрских складов Ozon.
  - `is_blr_traceable` — boolean. `true`, если товар отслеживаемый.
  - `last_changed_status_date` — object. Период, в который последний раз изменялся статус у отправлений.
    - `from` — string<date-time>. Дата начала периода.
    - `to` — string<date-time>. Дата окончания периода.
  - `order_id` — integer<int64>. Идентификатор заказа.
  - `order_numbers` — array[string]. Номера заказов, к которым относятся отправления.
  - `provider_ids` — array[string<int64>]. Идентификатор службы доставки. Можно получить с помощью метода [/v1/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodList).
  - `since` — string<date-time> **обязательный**. Дата начала периода, за который нужно получить список отправлений.
  - `statuses` — array[string]. Статус отправления: - `awaiting_registration` — ожидает регистрации; - `acceptance_in_progress` — идёт приёмка; - `awaiting_approve` — ожидает подтверждения; - `awaiting_packaging` — ожидает упаковки; - `awaiting_deliver` — ожидает отгрузки; - `arbitration` — арбитраж; - `client_arbitration` — клиентский арбитраж доставки; - `delivering` — доставляется; - `driver_pickup` — у водителя; - `delivered` — доставлено; - `cancelled` — отменено; - `not_accepted` — не принято на сортировочном центре; - `sent_by_seller` – отправлено продавцом.
  - `to` — string<date-time> **обязательный**. Дата конца периода, за который нужно получить список отправлений.
  - `warehouse_ids` — array[string<int64>]. Идентификатор склада. Можно получить с помощью метода [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList).
- `limit` — integer<int64> **обязательный**. Количество значений в ответе.
- `sort_dir` — string (ASC, DESC). Направление сортировки: - `ASC` — по возрастанию; - `DESC` — по убыванию.
- `translit` — boolean. `true`, чтобы включить транслитерацию адреса из кириллицы в латиницу.
- `with` — object. Дополнительные поля, которые нужно добавить в ответ.
  - `analytics_data` — boolean. `true`, чтобы добавить в ответ данные аналитики.
  - `barcodes` — boolean. `true`, чтобы добавить в ответ штрихкоды отправления.
  - `financial_data` — boolean. `true`, чтобы добавить в ответ финансовые данные.
  - `legal_info` — boolean. `true`, чтобы добавить в ответ юридическую информацию.

## Ответы

**200** — Список отправлений

- `cursor` — string. Указатель для выборки следующих данных.
- `has_next` — boolean. `true`, если в ответе вернулись не все отправления.
- `postings` — ?. Список отправлений.
  - `addressee` — object. Контактные данные получателя.
    - `name` — string. Имя получателя.
  - `analytics_data` — object. Данные аналитики.
    - `city` — string. Город доставки. Только для отправлений rFBS и продавцов из СНГ.
    - `client_delivery_date_begin` — string<date-time>. Дата и время начала доставки. Только для отправлений, оформленных через [Ozon Доставку](#tag/OzonLogistics).
    - `client_delivery_date_end` — string<date-time>. Ожидаемая дата, до которой заказ будет доставлен. Только для отправлений, оформленных через [Ozon Доставку](#tag/OzonLogistics).
    - `delivery_date_begin` — string<date-time>. Дата и время начала доставки.
    - `delivery_date_end` — string<date-time>. Дата и время конца доставки.
    - `delivery_type` — string. Способ доставки.
    - `is_legal` — boolean. `true`, если получатель юридическое лицо.
    - `is_premium` — boolean. `true`, если у получателя есть подписка Premium.
    - `payment_type_group_name` — string. Способ оплаты: - `картой онлайн`; - `карта Ozon Банка`; - `автосписание с карты Ozon Банка при выдаче`; - `сохранённой картой при получении`; - `Система Быстрых Платежей`; - `Ozon Рассрочка`; - `оплата на расчётный счёт`; - `SberPay`; - `предоплата на стороне внешнего продавца`.
    - `region` — string. Регион доставки. Только для отправлений rFBS.
    - `tpl_provider` — string. Служба доставки.
    - `tpl_provider_id` — integer<int64>. Идентификатор службы доставки.
    - `warehouse` — string. Название склада отправки заказа.
    - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `available_actions` — array[string]. Доступные действия и информация об отправлении: - `arbitration` — открыть спор; - `awaiting_delivery` — перевести в статус «Ожидает отгрузки»; - `can_create_chat` — начать чат с покупателем; - `cancel` — отменить отправление; - `click_track_number` — просмотреть по трек-номеру историю изменения статусов в личном кабинете; - `customer_phone_available` — телефон покупателя; - `has_weight_products` — весовые товары в отправлении; - `hide_region_and_city` — скрыть регион и город покупателя в отчёте; - `invoice_get` — получить информацию из счёта-фактуры; - `invoice_send` — создать счёт-фактуру; - `invoice_update` — отредактировать счёт-фактуру; - `label_download_big` — скачать большую этикетку; - `label_download_small` — скачать маленькую этикетку; - `label_download` — скачать этикетку; - `non_int_delivered` — перевести в статус «Условно доставлен»; - `non_int_delivering` — перевести в статус «Доставляется»; - `non_int_last_mile` — перевести в статус «Курьер в пути»; - `product_cancel` — отменить часть товаров в отправлении; - `set_cutoff` — укажите дату отгрузки методом [/v1/posting/cutoff/set](#operation/PostingAPI_SetPostingCutoff) не позже даты в параметре `shipment_date`; - `set_timeslot` — изменить время доставки покупателю; - `set_track_number` — указать или изменить трек-номер; - `ship_async_in_process` — отправление собирается; - `ship_async_retry` — собрать отправление повторно после ошибки сборки; - `ship_async` — собрать отправление; - `ship_with_additional_info` — заполните дополнительную информацию методом [/v6/fbs/posting/product/exemplar/set](https://docs.ozon.ru/api/seller/#operation/PostingAPI_FbsPostingProductExemplarSetV6); - `ship` — собрать отправление; - `update_cis` — изменить дополнительную информацию.
  - `barcodes` — object. Штрихкоды отправления.
    - `lower_barcode` — string. Нижний штрихкод на маркировке отправления.
    - `upper_barcode` — string. Верхний штрихкод на маркировке отправления.
  - `cancellation` — object. Информация об отмене.
    - `affect_cancellation_rating` — boolean. `true`, если отмена влияет на рейтинг продавца.
    - `cancel_reason` — string. Причина отмены.
    - `cancel_reason_id` — integer<int64>. Идентификатор причины отмены отправления.
    - `cancellation_initiator` — string. Инициатор отмены: - `Продавец`, - `Клиент`, - `Покупатель`, - `Ozon`, - `Система`, - `Служба доставки`.
    - `cancellation_type` — string. Тип отмены: - `seller` — отменено продавцом; - `client` или `customer` — отменено покупателем; - `ozon` — отменено Ozon; - `system` — отменено системой; - `delivery` — отменено службой доставки.
    - `cancelled_after_ship` — boolean. `true`, если отмена произошла после сборки отправления.
  - `customer` — object. Информация о покупателе.
    - `address` — object. Адрес доставки.
      - `address_tail` — string. Адрес в текстовом формате.
      - `city` — string. Город доставки.
      - `comment` — string. Комментарий к заказу.
      - `country` — string. Страна доставки.
      - `district` — string. Район доставки.
      - `latitude` — number<double>. Широта.
      - `longitude` — number<double>. Долгота.
      - `provider_pvz_code` — string. Код пункта выдачи заказов 3PL-провайдера.
      - `pvz_code` — integer<int64>. Код пункта выдачи заказов.
      - `region` — string. Регион доставки.
      - `zip_code` — string. Почтовый индекс получателя.
    - `customer_email` — string. Электронная почта покупателя.
    - `customer_id` — integer<int64>. Идентификатор покупателя.
    - `name` — string. Имя покупателя.
    - `phone` — string. Подменный контактный телефон покупателя.
  - `container` — object. Информация о грузоместе.
    - `cargo_type` — string (BOX, PALLET). Тип грузоместа: - `BOX` — коробка; - `PALLET` — палета. По умолчанию: `BOX`.
    - `container_date` — string. Дата создания грузоместа в часовом поясе склада.
    - `container_id` — integer<int64>. Идентификатор грузоместа.
    - `container_number` — integer<int32>. Порядковый номер грузоместа.
  - `container_sort_type` — string. Тип сортировки грузоместа: - `SORT` — сортируемый; - `NON-SORT` — несортируемый.
  - `delivering_date` — string<date-time>. Дата передачи отправления в доставку.
  - `delivery_method` — object. Информация о способе доставки.
    - `id` — integer<int64>. Идентификатор способа доставки.
    - `name` — string. Название способа доставки.
    - `tpl_provider` — string. Служба доставки.
    - `tpl_provider_id` — integer<int64>. Идентификатор службы доставки.
    - `warehouse` — string. Название склада.
    - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `delivery_schema` — string. Схема доставки: - `SDS` — идентификатор единого SKU; - `FBO` — идентификатор товара, который продаётся со склада Ozon; - `FBS` — идентификатор товара, который продаётся со склада FBS; - `Crossborder` — идентификатор товара, который продаётся из-за границы.
  - `destination_place_id` — integer<int64>. Идентификатор места назначения.
  - `destination_place_name` — string. Название места назначения.
  - `external_order` — object. Информация о заказе с внешней платформы.
    - `is_external` — boolean. `true`, если заказ с внешней платформы.
    - `platform_name` — string. Название платформы, с которой сделали заказ.
  - `financial_data` — object. Информация о стоимости товара, размере скидки, выплате и комиссии.
    - `cluster_from` — string. Код региона, откуда отправляется заказ.
    - `cluster_to` — string. Код региона, куда доставляется заказ.
    - `products` — array[object]. Список товаров в заказе.
      - `actions` — array[string]. Список акций.
      - `commission` — object. Комиссия за товар.
        - `amount` — number<double>. Размер комиссии за товар.
        - `currency` — string. Код валюты, в которой рассчитывалась комиссия.
        - `percent` — integer<int64>. Процент комиссии.
      - `customer_price` — object. Цена товара.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
      - `old_price` — number<double>. Цена до учёта скидок. На карточке товара отображается зачёркнутой.
      - `payout` — number<double>. Выплата продавцу.
      - `price` — number<double>. Цена товара с учётом акций, кроме акций за счёт Ozon.
      - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
      - `quantity` — integer<int64>. Количество товара в отправлении.
      - `total_discount_percent` — number<double>. Процент скидки.
      - `total_discount_value` — number<double>. Сумма скидки.
  - `in_process_at` — string<date-time>. Дата и время начала обработки отправления.
  - `is_click_and_collect` — boolean. `true`, если отправление доставляется методом «Самовывоз из магазина».
  - `is_express` — boolean. `true`, если использовалась быстрая доставка Ozon Express.
  - `is_multibox` — boolean. Признак, что в отправлении есть многокоробочный товар и нужно передать количество коробок для него: - `true` — до сборки передайте количество коробок через метод [/v3/posting/multiboxqty/set](#operation/PostingAPI_PostingMultiBoxQtySetV3). - `false` — отправление собрано с указанием количества коробок в параметре `multi_box_qty` или в отправлении нет многокоробочного товара.
  - `is_presortable` — boolean. `true`, если товар — пересорт.
  - `integration_type_flow` — string. Процесс обработки отправления: - `ozon` — доставка силами Ozon; - `aggregator` — доставка внешней службой, Ozon регистрирует заказ; - `non_integrated` — доставка силами продавца; - `3pl_tracking` — доставка внешней службой, продавец регистрирует заказ; - `hybrid` — гибридная интеграция; - `hybrid_aggregator` — гибридная интеграция с доставкой внешней службой, Ozon регистрирует заказ; - `hybrid_non_integrated` — гибридная интеграция с доставкой силами продавца; - `hybrid_3pl_tracking` — гибридная интеграция с доставкой внешней службой, продавец регистрирует заказ; - `click_and_collect` — бронирование в магазине партнёра; - `FBP` — доставка с партнёрских складов Ozon.
  - `legal_info` — object. Юридическая информация о покупателе.
    - `company_name` — string. Название компании.
    - `inn` — string. ИНН.
    - `kpp` — string. КПП.
  - `multi_box_qty` — integer<int32>. Количество коробок, в которые упакован товар.
  - `optional` — object. Список товаров с дополнительными характеристиками.
    - `products_with_possible_mandatory_mark` — array[string<int64>]. Список товаров с возможной маркировкой.
  - `order_id` — integer<int64>. Идентификатор заказа, к которому относится отправление.
  - `order_number` — string. Номер заказа, к которому относится отправление.
  - `parent_posting_number` — string. Номер родительского отправления, в результате разделения которого появилось текущее.
  - `pickup_code_verified_at` — string<date-time>. Дата и время успешной валидации кода курьера. Проверьте код курьера методом [/v1/posting/fbs/pick-up-code/verify](#operation/PostingAPI_PostingFBSPickupCodeVerify).
  - `posting_number` — string. Номер отправления.
  - `products` — array[object]. Список товаров в отправлении.
    - `imei` — array[string]. Список IMEI мобильных устройств.
    - `is_blr_traceable` — boolean. `true`, если товар отслеживаемый.
    - `is_marketplace_buyout` — boolean. `true`, если Ozon выкупил товар. [Подробнее о выкупе товаров в Базе знаний продавца](https://seller-edu.ozon.ru/commissions-tariffs/commissions-tariffs-ozon/prodaji-tovarov-v-eaes-i-drugie-strany#какие-товары-выкупает-ozon)
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — object. Цена товара.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `product_color` — string. Цвет товара.
    - `quantity` — integer<int32>. Количество товара в отправлении.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
    - `weight` — number<double>. Вес товара в упаковке.
  - `prr_option` — string. Код услуги погрузочно-разгрузочных работ: - `lift` — подъём на лифте; - `stairs` — подъём по лестнице; - `none` — покупатель отказался от услуги, поднимать товары не нужно; - `delivery_default` — доставка включена в стоимость, по условиям оферты нужно доставить товар на этаж. Для КГТ-отправлений с доставкой силами продавца или интегрированной службой.
  - `quantum_id` — integer<int64>. Идентификатор эконом-товара.
  - `require_blr_traceable_attrs` — boolean. `true`, если нужно заполнить атрибуты отслеживаемости.
  - `requirements` — object. Товары, для которых нужна дополнительная информация. Чтобы перевести отправление в следующий статус, передайте: - страну-изготовителя; - номер грузовой таможенной декларации (ГТД); - регистрационный номер партии товара (РНПТ); - маркировку «Честный знак»; - другие маркировки; - вес.
    - `products_requiring_change_country` — array[string<int64>]. Список идентификаторов товаров (SKU), для которых нужно изменить страну-изготовителя. Чтобы изменить страну-изготовителя, используйте методы [/v2/posting/fbs/product/country/list](#operation/PostingAPI_ListCountryProductFbsPostingV2) и [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).
    - `products_requiring_country` — array[string<int64>]. Список идентификаторов товаров (SKU), для которых нужно передать информацию о стране-изготовителе. Для сборки отправления передайте информацию о стране-изготовителе для всех перечисленных товаров методом [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).
    - `products_requiring_gtd` — array[string<int64>]. Список идентификаторов товаров (SKU), для которых нужно передать номера грузовой таможенной декларации (ГТД). До сборки отправления передайте для всех перечисленных товаров номер грузовой таможенной декларации или информацию о том, что номера нет, методом [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).
    - `products_requiring_imei` — array[string<int64>]. Список идентификаторов товаров, для которых нужно передать IMEI.
    - `products_requiring_jw_uin` — array[string<int64>]. Список товаров, для которых нужно передать уникальный идентификационный номер (УИН) ювелирного изделия. До сборки отправления передайте для всех перечисленных товаров УИН методом [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).
    - `products_requiring_mandatory_mark` — array[string<int64>]. Список идентификаторов товаров (SKU), для которых нужно передать маркировку «Честный знак». До сборки отправления передайте для всех перечисленных товаров маркировку «Честный знак» методом [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).
    - `products_requiring_rnpt` — array[string<int64>]. Список идентификаторов товаров (SKU), для которых нужно передать регистрационный номер партии товара (РНПТ). До сборки отправления передайте для всех перечисленных товаров РНПТ методом [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).
    - `products_requiring_weight` — array[string<int64>]. Список товаров, для которых нужно передать вес.
  - `shipment_date` — string<date-time>. Дата и время, до которой нужно собрать отправление. Показываем рекомендованное время отгрузки. По истечении этого времени начнёт применяться новый тариф, информацию о нём получите в поле `tariffication`.
  - `shipment_date_without_delay` — string<date-time>. Дата и время отгрузки без просрочки.
  - `sorting_center` — object. Информация о сортировочном центре, в который нужно привезти отправление. Для `integration_type_flow = hybrid_3pl_tracking`. Если значение `null`, информацию получить не удалось.
    - `code` — string. Код сортировочного центра.
    - `name` — string. Название сортировочного центра.
  - `status` — string. Статус отправления: - `acceptance_in_progress` — идёт приёмка; - `arbitration` — арбитраж; - `awaiting_approve` — ожидает подтверждения; - `awaiting_deliver` — ожидает отгрузки; - `awaiting_packaging` — ожидает упаковки; - `awaiting_registration` — ожидает регистрации; - `awaiting_verification` — создано; - `cancelled` — отменено; - `cancelled_from_split_pending` — отменено из-за разделения отправления; - `client_arbitration` — клиентский арбитраж доставки; - `delivering` — доставляется; - `driver_pickup` — у водителя; - `not_accepted` — не принято на сортировочном центре.
  - `substatus` — string. Подстатус отправления: - `posting_acceptance_in_progress`— идёт приёмка; - `posting_in_arbitration` — арбитраж; - `posting_created` — создано; - `posting_in_carriage` — в перевозке; - `posting_not_in_carriage` — не добавлено в перевозку; - `posting_registered` — зарегистрировано; - `posting_transferring_to_delivery`, если `status=awaiting_deliver` — передаётся в доставку; - `posting_awaiting_passport_data` — ожидает паспортных данных; - `posting_created` — создано; - `posting_awaiting_registration` — ожидает регистрации; - `posting_registration_error` — ошибка регистрации; - `posting_transferring_to_delivery`, если `status=awaiting_registration` — передаётся курьеру; - `posting_split_pending` — создано; - `posting_canceled` — отменено; - `posting_in_client_arbitration` — клиентский арбитраж доставки; - `posting_delivered` — доставлено; - `posting_received` — получено; - `posting_conditionally_delivered` — условно доставлено; - `posting_in_courier_service` — курьер в пути; - `posting_in_pickup_point` — в пункте выдачи; - `posting_on_way_to_city` — в пути в ваш город; - `posting_on_way_to_pickup_point` — в пути в пункт выдачи; - `posting_returned_to_warehouse` — возвращено на склад; - `posting_transferred_to_courier_service` — передаётся в службу доставки; - `posting_driver_pick_up` — у водителя; - `posting_not_in_sort_center` — не принято на сортировочном центре; - `ship_failed` — сборка не удалась.
  - `tariffication` — object. Информация по тарификации отгрузки.
    - `current_tariff_charge` — object. Скидка или надбавка.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `current_tariff_min_charge` — object. Минимальная скидка или надбавка.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `current_tariff_rate` — number<double>. Процент тарификации.
    - `current_tariff_type` — string. Тип тарификации — скидка или надбавка.
    - `next_tariff_charge` — object. Скидка или надбавка через время из параметра `next_tariff_starts_at`.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `next_tariff_min_charge` — object. Минимальная скидка или надбавка через время из параметра `next_tariff_starts_at`.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `next_tariff_rate` — number<double>. Процент, по которому будет тарифицироваться отправление через время из параметра `next_tariff_starts_at`.
    - `next_tariff_starts_at` — string<date-time>. Дата и время, когда начнёт применяться новый тариф.
    - `next_tariff_type` — string. Тип тарификации через время из параметра `next_tariff_starts_at` — скидка или надбавка.
  - `tariffication_steps` — array[object]. Этапы тарификации.
    - `min_charge` — object. Минимальная скидка или надбавка.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `tariff_charge` — object. Скидка или надбавка.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `tariff_deadline_at` — string<date-time>. Дата и время окончания этапа тарификации. После этой даты автоматически начинается следующий этап.
    - `tariff_rate` — number<double>. Процент скидки или надбавки.
    - `tariff_type` — string. Тип тарификации.
  - `tpl_integration_type` — string. Тип интеграции со службой доставки: - `ozon` — доставка службой Ozon; - `3pl_tracking` — доставка интегрированной службой; - `non_integrated` — доставка сторонней службой; - `aggregator` — доставка через партнёрскую доставку Ozon; - `hybryd` — схема доставки Почты России.
  - `tracking_number` — string. Трек-номер отправления.
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
