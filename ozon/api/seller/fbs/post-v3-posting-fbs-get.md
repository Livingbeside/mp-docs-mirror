---
title: Получить информацию об отправлении по идентификатору
api: ozon-seller
method: POST
path: /v3/posting/fbs/get
operation_id: PostingAPI_GetFbsPostingV3
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 50bcccdc8337c9d4
---

# Получить информацию об отправлении по идентификатору

`POST /v3/posting/fbs/get`

Чтобы получать актуальную дату отгрузки, регулярно обновляйте информацию об отправлениях или подключите [пуш-уведомления](#tag/push_start).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Идентификатор отправления.
- `with` — object. Дополнительные поля, которые нужно добавить в ответ.
  - `analytics_data` — boolean. Добавить в ответ данные аналитики.
  - `barcodes` — boolean. Добавить в ответ штрихкоды отправления.
  - `financial_data` — boolean. Добавить в ответ финансовые данные.
  - `legal_info` — boolean. Добавить в ответ юридическую информацию.
  - `product_exemplars` — boolean. Добавить в ответ данные о продуктах и их экземплярах.
  - `related_postings` — boolean. Добавить в ответ номера связанных отправлений. Связанные отправления — те, на которое было разделено родительское отправление при сборке.
  - `translit` — boolean. Выполнить транслитерацию возвращаемых значений.

## Ответы

**200** — Информация об отправлении

- `result` — object. Информация об отправлении.
  - `additional_data` — array[object]
    - `key` — string
    - `value` — string
  - `addressee` — object. Контактные данные получателя.
    - `name` — string. Имя покупателя.
    - `phone` — string. Подменный контактный телефон получателя. [Подробнее о подменных номерах в Базе знаний](https://seller-edu.ozon.ru/rfbs/orders-cancellations/replacement-number)
    - `pin` — string. Добавочный номер телефона получателя, вводится в тональном режиме. Только для отправлений realFBS со службами доставки: - `3pl_tracking` — доставка внешней службой, продавец регистрирует заказ. - `non_integrated` — доставка силами продавца.
  - `analytics_data` — object. Данные аналитики.
    - `city` — string. Город доставки. Только для отправлений rFBS и продавцов из СНГ.
    - `client_delivery_date_begin` — string<date-time>. Дата и время начала доставки. Только для отправлений, оформленных через [Ozon Доставку](#tag/OzonLogistics).
    - `client_delivery_date_end` — string<date-time>. Ожидаемая дата, до которой заказ будет доставлен. Только для отправлений, оформленных через [Ozon Доставку](#tag/OzonLogistics).
    - `delivery_date_begin` — string<date-time>. Дата и время начала доставки.
    - `delivery_date_end` — string<date-time>. Дата и время конца доставки.
    - `delivery_type` — string. Способ доставки.
    - `is_legal` — boolean. Признак, что получатель юридическое лицо: - `true` — юридическое лицо, - `false` — физическое лицо.
    - `is_premium` — boolean. Наличие подписки Premium.
    - `payment_type_group_name` — string. Способ оплаты: - `картой онлайн`, - `карта Ozon Банка`, - `автосписание с карты Ozon Банка при выдаче`, - `сохранённой картой при получении`, - `Система Быстрых Платежей`, - `Ozon Рассрочка`, - `оплата на расчётный счёт`, - `SberPay`, - `предоплата на стороне внешнего продавца`.
    - `region` — string. Регион доставки. Только для отправлений rFBS.
    - `tpl_provider` — string. Служба доставки.
    - `tpl_provider_id` — integer<int64>. Идентификатор службы доставки.
    - `warehouse` — string. Название склада отправки заказа.
    - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `available_actions` — ?. Доступные действия и информация об отправлении: - `arbitration` — открыть спор; - `awaiting_delivery` — перевести в статус «Ожидает отгрузки»; - `can_create_chat` — начать чат с покупателем; - `cancel` — отменить отправление; - `click_track_number` — просмотреть по трек-номеру историю изменения статусов в личном кабинете; - `customer_phone_available` — телефон покупателя; - `has_weight_products` — весовые товары в отправлении; - `hide_region_and_city` — скрыть регион и город покупателя в отчёте; - `invoice_get` — получить информацию из счёта-фактуры; - `invoice_send` — создать счёт-фактуру; - `invoice_update` — отредактировать счёт-фактуру; - `label_download_big` — скачать большую этикетку; - `label_download_small` — скачать маленькую этикетку; - `label_download` — скачать этикетку; - `non_int_delivered` — перевести в статус «Условно доставлен»; - `non_int_delivering` — перевести в статус «Доставляется»; - `non_int_last_mile` — перевести в статус «Курьер в пути»; - `product_cancel` — отменить часть товаров в отправлении; - `set_cutoff` — необходимо указать дату отгрузки, воспользуйтесь методом [/v1/posting/cutoff/set](#operation/PostingAPI_SetPostingCutoff); - `set_timeslot` — изменить время доставки покупателю; - `set_track_number` — указать или изменить трек-номер; - `ship_async_in_process` — отправление собирается; - `ship_async_retry` — собрать отправление повторно после ошибки сборки; - `ship_async` — собрать отправление; - `ship_with_additional_info` — необходимо заполнить дополнительную информацию; - `ship` — собрать отправление; - `update_cis` — изменить дополнительную информацию.
  - `barcodes` — object. Штрихкоды отправления.
    - `lower_barcode` — string. Нижний штрихкод на маркировке отправления.
    - `upper_barcode` — string. Верхний штрихкод на маркировке отправления.
  - `cancellation` — object. Информация об отмене.
    - `affect_cancellation_rating` — boolean. Если отмена влияет на рейтинг продавца — `true`.
    - `cancel_reason` — string. Причина отмены.
    - `cancel_reason_id` — integer<int64>. Идентификатор причины отмены отправления.
    - `cancellation_initiator` — string. Инициатор отмены: - `Продавец`, - `Клиент` или `покупатель`, - `Ozon`, - `Система`, - `Служба доставки`.
    - `cancellation_type` — string. Тип отмены отправления: - `seller` — отменено продавцом; - `client` или `customer` — отменено покупателем; - `ozon` — отменено Ozon; - `system`— отменено системой; - `delivery` — отменено службой доставки.
    - `cancelled_after_ship` — boolean. Если отмена произошла после сборки отправления — `true`.
  - `container` — object. Информация о грузоместе.
    - `cargo_type` — string (BOX, PALLET). Тип грузоместа: - `BOX` — коробка; - `PALLET` — палета. По умолчанию: `BOX`.
    - `container_date` — string. Дата создания грузоместа в часовом поясе склада.
    - `container_id` — integer<int64>. Идентификатор грузоместа.
    - `container_number` — integer<int32>. Порядковый номер грузоместа.
  - `container_sort_type` — string. Тип сортировки грузоместа: - `SORT` — сортируемый; - `NON-SORT` — несортируемый.
  - `courier` — object. Данные о курьере.
    - `car_model` — string. Модель автомобиля.
    - `car_number` — string. Номер автомобиля.
    - `name` — string. Полное имя курьера.
    - `phone` — string. Телефон курьера. Всегда возвращает пустую строку `""`.
  - `customer` — object. Данные о покупателе.
    - `address` — object. Информация об адресе доставки.
      - `address_tail` — string. Адрес в текстовом формате.
      - `city` — string. Город доставки.
      - `comment` — string. Комментарий к заказу.
      - `country` — string. Страна доставки.
      - `district` — string. Район доставки.
      - `latitude` — number<double>. Широта.
      - `longitude` — number<double>. Долгота.
      - `provider_pvz_code` — string. Код пункта выдачи заказов 3PL провайдера.
      - `pvz_code` — integer<int64>. Код пункта выдачи заказов.
      - `region` — string. Регион доставки.
      - `zip_code` — string. Почтовый индекс получателя.
    - `customer_id` — integer<int64>. Идентификатор покупателя.
    - `name` — string. Имя покупателя.
    - `phone` — string. Подменный контактный телефон покупателя. [Подробнее о подменных номерах в Базе знаний](https://seller-edu.ozon.ru/rfbs/orders-cancellations/replacement-number)
  - `delivering_date` — string<date-time>. Дата передачи отправления в доставку.
  - `delivery_method` — object. Метод доставки.
    - `id` — integer<int64>. Идентификатор способа доставки.
    - `name` — string. Название способа доставки.
    - `tpl_provider` — string. Служба доставки.
    - `tpl_provider_id` — integer<int64>. Идентификатор службы доставки.
    - `warehouse` — string. Название склада.
    - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `delivery_price` — string. Стоимость доставки.
  - `external_order` — object. Информация о заказе с внешней платформы.
    - `is_external` — boolean. `true`, если заказ с внешней платформы.
    - `platform_name` — string. Название платформы, с которой сделали заказ.
  - `fact_delivery_date` — string<date-time>. Дата фактической передачи отправления в доставку.
  - `financial_data` — object. Данные о стоимости товара, размере скидки, выплате и комиссии.
    - `cluster_from` — string. Код региона, откуда отправляется заказ.
    - `cluster_to` — string. Код региона, куда доставляется заказ.
    - `products` — array[object]. Список товаров в заказе.
      - `actions` — array[string]. Список акций.
      - `commission_amount` — number<double>. Размер комиссии за товар.
      - `commission_percent` — integer<int64>. Процент комиссии.
      - `commissions_currency_code` — string. Код валюты, в которой рассчитывались комиссии.
      - `currency_code` — string. Валюта ваших цен. Cовпадает с валютой, которая установлена в настройках личного кабинета. Возможные значения: - `RUB` — российский рубль, - `BYN` — белорусский рубль, - `KZT` — тенге, - `EUR` — евро, - `USD` — доллар США, - `CNY` — юань.
      - `customer_currency_code` — string. Код валюты покупателя.
      - `customer_price` — number<double>. Цена товара для покупателя с учётом скидок продавца и Ozon.
      - `old_price` — number<double>. Цена до учёта скидок. На карточке товара отображается зачёркнутой.
      - `payout` — number<double>. Выплата продавцу.
      - `price` — number<double>. Цена товара с учётом акций, кроме акций за счёт Ozon.
      - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
      - `quantity` — integer<int64>. Количество товара в отправлении.
      - `total_discount_percent` — number<double>. Процент скидки.
      - `total_discount_value` — number<double>. Сумма скидки.
  - `in_process_at` — string<date-time>. Дата и время начала обработки отправления.
  - `integration_type_flow` — string. Процесс обработки отправления: - `ozon` — доставка силами Ozon; - `aggregator` — доставка внешней службой, Ozon регистрирует заказ; - `non_integrated` — доставка силами продавца; - `3pl_tracking` — доставка внешней службой, продавец регистрирует заказ; - `hybrid` — гибридная интеграция; - `hybrid_aggregator` — гибридная интеграция с доставкой внешней службой, Ozon регистрирует заказ; - `hybrid_non_integrated` — гибридная интеграция с доставкой силами продавца; - `hybrid_3pl_tracking` — гибридная интеграция с доставкой внешней службой, продавец регистрирует заказ; - `click_and_collect` — бронирование в магазине партнёра; - `FBP` — доставка с партнёрских складов Ozon.
  - `is_express` — boolean. Если использовалась быстрая доставка Ozon Express — `true`.
  - `is_multibox` — boolean. Признак, что в отправлении есть многокоробочный товар и нужно передать количество коробок для него: - `true` — до сборки передайте количество коробок через метод [/v3/posting/multiboxqty/set](#operation/PostingAPI_PostingMultiBoxQtySetV3). - `false` — отправление собрано с указанием количества коробок в параметре `multi_box_qty` или в отправлении нет многокоробочного товара.
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
  - `pickup_code_verified_at` — string<date-time>. Дата и время успешной валидации кода курьера. Чтобы проверить код курьера, воспользуйтесь методом [/v1/posting/fbs/pick-up-code/verify](#operation/PostingAPI_PostingFBSPickupCodeVerify).
  - `posting_number` — string. Номер отправления.
  - `previous_substatus` — string. Предыдущий подстатус отправления. Возможные значения: - `posting_acceptance_in_progress` — идёт приёмка, - `posting_in_arbitration` — арбитраж, - `posting_created` — создано, - `posting_in_carriage` — в перевозке, - `posting_not_in_carriage` — не добавлено в перевозку, - `posting_registered` — зарегистрировано, - `posting_transferring_to_delivery` (`status=awaiting_deliver`) — передаётся в доставку, - `posting_awaiting_passport_data` — ожидает паспортных данных, - `posting_created` — создано, - `posting_awaiting_registration` — ожидает регистрации, - `posting_registration_error` — ошибка регистрации, - `posting_transferring_to_delivery` (`status=awaiting_registration`) — передаётся курьеру, - `posting_split_pending` — создано, - `posting_canceled` — отменено, - `posting_in_client_arbitration` — клиентский арбитраж доставки, - `posting_delivered` — доставлено, - `posting_received` — получено, - `posting_conditionally_delivered` — условно доставлено, - `posting_in_courier_service` — курьер в пути, - `posting_in_pickup_point` — в пункте выдачи, - `posting_on_way_to_city` — в пути в ваш город, - `posting_on_way_to_pickup_point` — в пути в пункт выдачи, - `posting_returned_to_warehouse` — возвращено на склад, - `posting_transferred_to_courier_service` — передаётся в службу доставки, - `posting_driver_pick_up` — у водителя, - `posting_not_in_sort_center` — не принято на сортировочном центре.
  - `product_exemplars` — object. Информация по продуктам и их экземплярам. Ответ содержит поле `product_exemplars`, если в запросе передан признак `with.product_exemplars = true`.
    - `products` — array[object]. Информация по продуктам.
      - `exemplars` — array[object]. Информация по экземплярам.
        - `exemplar_id` — integer<int64>. Идентификатор экземпляра.
        - `gtd` — string. Номер грузовой таможенной декларации (ГТД).
        - `imei` — array[string]. Список IMEI мобильных устройств.
        - `is_gtd_absent` — boolean. Признак того, что не указан номер таможенной декларации.
        - `is_rnpt_absent` — boolean. Признак того, что не указан регистрационный номер партии товара (РНПТ).
        - `mandatory_mark` — string. Обязательная маркировка «Честный ЗНАК».
        - `rnpt` — string. Регистрационный номер партии товара (РНПТ).
        - `weight` — number<float>. Фактический вес экземпляра.
      - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `products` — array[object]. Массив товаров в отправлении.
    - `currency_code` — string. Валюта ваших цен. Совпадает с валютой, которая установлена в настройках личного кабинета. Возможные значения: - `RUB` — российский рубль, - `BYN` — белорусский рубль, - `KZT` — тенге, - `EUR` — евро, - `USD` — доллар США, - `CNY` — юань.
    - `dimensions` — object. Размеры товара.
      - `height` — string. Высота упаковки.
      - `length` — string. Длина товара.
      - `weight` — string. Вес товара в упаковке.
      - `width` — string. Ширина упаковки.
    - `has_imei` — boolean. Признак наличия IMEI. Если IMEI есть — `true`.
    - `is_blr_traceable` — boolean. Признак прослеживаемости товара.
    - `is_marketplace_buyout` — boolean. `true`, если Ozon выкупил товар. [Подробнее о выкупе товаров в Базе знаний продавца](https://seller-edu.ozon.ru/commissions-tariffs/commissions-tariffs-ozon/prodaji-tovarov-v-eaes-i-drugie-strany#какие-товары-выкупает-ozon)
    - `is_weight_needed` — boolean. `true`, если товар весовой.
    - `jw_uin` — array of strings. Уникальный идентификационный номер (УИН) ювелирного изделия.
    - `mandatory_mark` — array[string]. Обязательная маркировка товара.
    - `name` — string. Название.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — string. Цена товара с учётом скидок — это значение показывается на карточке товара.
    - `quantity` — integer<int32>. Количество товара.
    - `sku` — integer<int64>. Идентификатор товара на Ozon.
    - `weight_max` — number<float>. Максимальный вес экземпляра.
    - `weight_min` — number<float>. Минимальный вес экземпляра.
  - `provider_status` — string. Статус службы доставки.
  - `prr_option` — object. Информация об услуге погрузочно-разгрузочных работ. Актуально для КГТ-отправлений с доставкой силами продавца или интегрированной службой.
    - `code` — string. Код услуги погрузочно-разгрузочных работ: - `lift` — подъём на лифте. - `stairs` — подъём по лестнице. - `none` — покупатель отказался от услуги, поднимать товары не нужно. - `delivery_default` — доставка включена в стоимость, по условиям оферты нужно доставить товар на этаж.
    - `currency_code` — string. Валюта.
    - `floor` — string. Этаж, на который нужно поднять товар.
    - `price` — string. Стоимость услуги, которую Ozon компенсирует продавцу.
  - `related_postings` — object. Связанные отправления.
    - `related_posting_numbers` — ?. Список номеров связанных отправлений.
  - `related_weight_postings` — array[string]. Список номеров связанных весовых отправлений.
  - `require_blr_traceable_attrs` — boolean. `true`, если нужно заполнить атрибуты прослеживаемости.
  - `requirements` — object. Cписок продуктов, для которых нужно передать страну-изготовителя, номер грузовой таможенной декларации (ГТД), регистрационный номер партии товара (РНПТ), маркировку «Честный ЗНАК», другие маркировки или вес, чтобы перевести отправление в следующий статус.
    - `products_requiring_change_country` — array[string<int64>]. Список идентификаторов товаров (SKU), для которых нужно изменить страну-изготовитель. Чтобы изменить страну-изготовитель, используйте методы [/v2/posting/fbs/product/country/list](#operation/PostingAPI_ListCountryProductFbsPostingV2) и [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).
    - `products_requiring_country` — array[string<int64>]. Список идентификаторов товаров (SKU), для которых нужно передать информацию о стране-изготовителе. Для сборки отправления передайте информацию о стране-изготовителе для всех перечисленных товаров с помощью метода [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).
    - `products_requiring_gtd` — array[string<int64>]. Список идентификаторов товаров (SKU), для которых нужно передать номера таможенной декларации (ГТД). До сборки отправления передайте для всех перечисленных товаров номер таможенной декларации или информацию о том, что номера нет, методом [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).
    - `products_requiring_imei` — array[string<int64>]. Список идентификаторов товаров, для которых нужно передать IMEI.
    - `products_requiring_jw_uin` — array[string<int64>]. Список товаров, для которых нужно передать уникальный идентификационный номер (УИН) ювелирного изделия. До сборки отправления передайте для всех перечисленных товаров уникальный идентификационный номер (УИН) методом [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).
    - `products_requiring_mandatory_mark` — array[string<int64>]. Список идентификаторов товаров (SKU), для которых нужно передать маркировку «Честный ЗНАК». До сборки отправления передайте для всех перечисленных товаров маркировку «Честный ЗНАК» методом [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).
    - `products_requiring_rnpt` — array[string<int64>]. Список идентификаторов товаров (SKU), для которых нужно передать регистрационный номер партии товара (РНПТ). До сборки отправления передайте для всех перечисленных товаров регистрационный номер партии товара (РНПТ) методом [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).
    - `products_requiring_weight` — array[string<int64>]. Список товаров, для которых нужно передать вес.
  - `shipment_date` — string<date-time>. Дата и время, до которой необходимо собрать отправление. Показываем рекомендованное время отгрузки. По истечении этого времени начнёт применяться новый тариф, информацию о нём уточняйте в поле `tariffication`.
  - `shipment_date_without_delay` — string<date-time>. Дата и время отгрузки без просрочки.
  - `sorting_center` — object. Информация о сортировочном центре, в который нужно привезти отправление. Для `integration_type_flow = hybrid_3pl_tracking`. Если значение `null`, информацию получить не удалось.
    - `code` — string. Код сортировочного центра.
    - `name` — string. Название сортировочного центра.
  - `status` — string. Статус отправления: - `acceptance_in_progress` — идёт приёмка, - `arbitration` — арбитраж, - `awaiting_approve` — ожидает подтверждения, - `awaiting_deliver` — ожидает отгрузки, - `awaiting_packaging` — ожидает упаковки, - `awaiting_registration` — ожидает регистрации, - `awaiting_verification` — создано, - `cancelled` — отменено, - `cancelled_from_split_pending` — отменён из-за разделения отправления, - `client_arbitration` — клиентский арбитраж доставки, - `delivered` — доставлено, - `delivering` — доставляется, - `driver_pickup` — у водителя, - `not_accepted` — не принят на сортировочном центре,
  - `substatus` — string. Подстатус отправления: - `posting_acceptance_in_progress` — идёт приёмка, - `posting_in_arbitration` — арбитраж, - `posting_created` — создано, - `posting_in_carriage` — в перевозке, - `posting_not_in_carriage` — не добавлено в перевозку, - `posting_registered` — зарегистрировано, - `posting_transferring_to_delivery` (`status=awaiting_deliver`) — передаётся в доставку, - `posting_awaiting_passport_data` — ожидает паспортных данных, - `posting_created` — создано, - `posting_awaiting_registration` — ожидает регистрации, - `posting_registration_error` — ошибка регистрации, - `posting_transferring_to_delivery` (`status=awaiting_registration`) — передаётся курьеру, - `posting_split_pending` — создано, - `posting_canceled` — отменено, - `posting_in_client_arbitration` — клиентский арбитраж доставки, - `posting_delivered` — доставлено, - `posting_received` — получено, - `posting_conditionally_delivered` — условно доставлено, - `posting_in_courier_service` — курьер в пути, - `posting_in_pickup_point` — в пункте выдачи, - `posting_on_way_to_city` — в пути в ваш город, - `posting_on_way_to_pickup_point` — в пути в пункт выдачи, - `posting_returned_to_warehouse` — возвращено на склад, - `posting_transferred_to_courier_service` — передаётся в службу доставки, - `posting_driver_pick_up` — у водителя, - `posting_not_in_sort_center` — не принято на сортировочном центре, - `ship_failed` — сборка не удалась.
  - `tariffication` — object. Информация по тарификации отгрузки.
    - `current_tariff_charge` — string. Текущая сумма скидки или надбавки.
    - `current_tariff_charge_currency_code` — string. Валюта суммы.
    - `current_tariff_rate` — number<double>. Текущий процент тарификации.
    - `current_tariff_type` — string. Текущий тип тарификации — скидка или надбавка.
    - `next_tariff_charge` — string. Сумма скидки или надбавки на следующем шаге тарификации.
    - `next_tariff_charge_currency_code` — string. Валюта нового тарифа.
    - `next_tariff_rate` — number<double>. Процент, по которому будет тарифицироваться отправление через указанное в параметре `next_tariff_starts_at` время.
    - `next_tariff_starts_at` — string<date-time>. Дата и время, когда начнёт применяться новый тариф. Формат: `YYYY-MM-DDThh:mm:ss.mcsZ`. Пример: `2023-11-13T08:05:57.657Z`.
    - `next_tariff_type` — string. Тип тарифа, по которому будет тарифицироваться отправление через указанное в параметре `next_tariff_starts_at` время — скидка или надбавка.
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
  - `tpl_integration_type` — string. Тип интеграции со службой доставки: - `ozon` — доставка через Ozon логистику. - `aggregator` — доставка внешней службой, Ozon регистрирует заказ. - `3pl_tracking` — доставка внешней службой, продавец регистрирует заказ. - `non_integrated` — доставка силами продавца.
  - `tracking_number` — string. Трек-номер отправления.

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
