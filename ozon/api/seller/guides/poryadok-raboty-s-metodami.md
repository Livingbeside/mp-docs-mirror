---
title: Порядок работы с методами
api: ozon-seller
tag: Process
group: Общее описание
kind: guide
source: "https://docs.ozon.ru/api/seller/"
content_sha: 95c00f608a84a5b3
---

# Порядок работы с методами

Если от вашего имени поступает много одинаковых или ошибочных запросов, мы можем ограничить
доступ к Seller API без предупреждения. 

 Вы можете отправить не больше 50 запросов в секунду на все методы с одного Client ID.

# Выгрузите атрибуты и характеристики Ozon

Чтобы методы для работы с товарами работали корректно, сопоставьте ваши категории и
характеристики со значениями в системе Ozon.

Если в методе [/v3/product/import](#operation/ProductAPI_ImportProductsV3) вы передадите значения не из справочника
Ozon, товар не будет создан или обновлён.

1. [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree) — получите список категорий и типов в виде дерева и используйте
 значение последнего уровня выбранной категории.

2. [/v1/description-category/attribute](#operation/DescriptionCategoryAPI_GetAttributes) — получите характеристики для выбранных
 категории и типа.

3. [/v1/description-category/attribute/values](#operation/DescriptionCategoryAPI_GetAttributeValues) — получите список значений для выбранной
 характеристики.

# Загрузите и обновите товары

После сравнения своих атрибутов и характеристик с атрибутной моделью Ozon можете приступить к загрузке товаров:

1. [/v3/product/import](#operation/ProductAPI_ImportProductsV3) — загрузите товары и услуги. Этот метод также позволяет
 обновить уже загруженные товары. В запросе устанавливается первичная цена и загружаются изображения товара. 

 В одном запросе можно передать до 100 товаров. Изображения загружаются прямой ссылкой на облачное хранилище, где они
 хранятся.

 В результате работы метода вы получите `task_id` — номер задания на загрузку товаров.

2. [/v1/product/import/info](#operation/ProductAPI_GetImportProductsInfo) — проверьте `task_id`, который вы получили при
 загрузке товаров. Метод вернёт информацию, успешно ли загрузились товары или при импорте была ошибка.

 Если ответ содержит статус, что товар на модерации, подождите её результатов и проверьте статус товара повторно.
 Обычно модерация занимает меньше одного дня.

3. [/v3/product/list](#operation/ProductAPI_GetProductList) — получите список созданных товаров после загрузки товаров.

 Метод позволяет использовать фильтры, чтобы разбить товары на группы по статусу видимости или отслеживать изменение
 их статуса с помощью идентификатора товара.

 Метод возвращает пару значений `offer_id` и `product_id` — они нужны практически во всех запросах для идентификации
 товара, с которым будет производиться действие. Если вы загружали товары через шаблон, используйте этот метод для
 получения `offer_id` и `product_id`, чтобы в дальнейшем работать по API с товарами.

## Загрузите и обновите изображения товара

Чтобы добавить изображения товара или заменить существующие, используйте:

1. [/v2/product/pictures/import](#operation/ProductImportPicturesV2) — загрузите или обновите изображения
 товара. Передайте прямые ссылки на изображения, загруженные в облачное хранилище.
2. [/v2/product/pictures/info](#operation/ProductAPI_ProductInfoPicturesV2) — проверьте статус загрузки.

## Обновите товар

Чтобы обновить информацию о товаре и его характеристики, используйте [/v3/product/import](#operation/ProductAPI_ImportProductsV3).

Если нужно обновить только характеристики товара, используйте [/v1/product/attributes/update](#operation/ProductAPI_ProductUpdateAttributes). Метод позволяет добавить дополнительную информацию к товару, чтобы карточка товара была более полной.

## Получите информацию о товаре

- [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) — получите информацию о товаре, например штрихкод, цену
 главного предложения, идентификатор категории, комиссию или ошибки модерации.
 С помощью фильтров [/v3/product/list](#operation/ProductAPI_GetProductList) получите список пакетно по всем товарам сразу или по категориям.

- [/v4/product/info/attributes](#operation/ProductAPI_GetProductAttributesV4) — получите описание характеристик товара.

- [/v1/product/info/description](#operation/ProductAPI_GetProductInfoDescription) — получите название и описание товара.

- [/v1/product/info/discounted](#operation/ProductAPI_GetProductInfoDiscounted) — получите информацию об уценке и
 основном товаре по SKU уценённого товара.

## Удалите или архивируйте товар

1. [/v2/products/delete](#operation/ProductAPI_DeleteProducts) — удалите товар, если он загрузился с ошибкой и попал в
 архив без SKU. Товары, которые успешно прошли модерацию и получили SKU, удалить из архива нельзя.

2. [/v1/product/archive](#operation/ProductAPI_ProductArchive) — перенесите товар в архив. Перед архивированием товара
 обнулите его остатки.

3. [/v1/product/unarchive](#operation/ProductAPI_ProductUnarchive) — верните товар из архива.

Товар попадёт в продажу, только когда вы установите его остаток.

# Загрузите сертификаты качества

## Информация о сертификатах

- Получите список типов сертификатов: [/v1/product/certificate/types](#operation/ProductAPI_ProductCertificateTypes).
- Получите список сертифицируемых категорий: [/v2/product/certification/list](#operation/ProductAPI_ProductCertificationList).
- Получите список статусов сертификата: [/v1/product/certificate/status/list](#operation/CertificateStatusList).
- Получите список типов соответствия требованиям: [/v2/product/certificate/accordance-types/list](#operation/CertificateAccordanceTypes).
- Получите список причин отклонения сертификата: [v1/product/certificate/rejection_reasons/list](#operation/RejectionReasonsList).
- Получите список сертификатов: [v1/product/certificate/list](#operation/CertificateList), используя фильтры:
 - тип сертификата `type` — значение `value` из ответа [/v1/product/certificate/types](#operation/ProductAPI_ProductCertificateTypes);
 - статус сертификата `status` — значение `code` из ответа [v1/product/certificate/status/list](#operation/CertificateStatusList).

## Работа с товарами сертификата

Чтобы привязать сертификат к товару:
1. Получите список брендов, для которых требуется предоставить сертификат: [/v1/brand/company-certification/list](#operation/BrandAPI_BrandCompanyCertificationList).
 В ответе вернутся бренды, товары которых есть в вашем личном кабинете.
 Список брендов может изменяться, если Ozon получит требование от бренда предоставлять сертификат.
2. Добавьте сертификаты для товаров: [/v1/product/certificate/create](#operation/ProductAPI_ProductCertificateCreate).
3. Привяжите сертификат к товару: [/v1/product/certificate/bind](#operation/ProductAPI_ProductCertificateBind).

Чтобы посмотреть список товаров, привязанных к сертификату, воспользуйтесь методом [v1/product/certificate/products/list](#operation/CertificateProductsList).
Если нужно получить список товаров с определённым статусом, в параметре `status` передайте значение `code` из ответа [v1/product/certificate/product_status/list](#operation/ProductStatusList).

Чтобы отвязать товар от сертификата, используйте [/v1/product/certificate/products/unbind](#operation/CertificateUnbind).

## Управление состоянием сертификата

Чтобы получить атрибуты для управления сертификатом:
1. Получите список типов сертификатов: [/v1/product/certificate/types](#operation/ProductAPI_ProductCertificateTypes).
2. Получите список типов соответствия требованиям: [/v2/product/certificate/accordance-types/list](#operation/CertificateAccordanceTypes).

Для создания сертификата используйте [/v1/product/certificate/create](#operation/ProductAPI_ProductCertificateCreate), передав в запросе:
- тип сертификата `type_code` — значение `value` из ответа [/v1/product/certificate/types](#operation/ProductAPI_ProductCertificateTypes);
- тип соответствия требованиям `accordance_type_code` — значение `code` из ответа [/v2/product/certificate/accordance-types/list](#operation/CertificateAccordanceTypes).

Чтобы удалить сертификат, используйте [/v1/product/certificate/delete](#operation/CertificateDelete).

# Обновите цены и остатки товаров

После загрузки товаров для схем FBS и rFBS можно перейти к обновлению остатков. Для схемы FBO остатки обновляются
автоматически по факту продажи.

Для обновления остатков используйте метод [/v2/products/stocks](#operation/ProductAPI_ProductsStocksV2). 
В этом методе дополнительно указывается идентификатор склада, на котором необходимо изменить остатки.

Для получения информации о количестве остатков для FBO, FBS, rFBS и FBP
используйте [/v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks).

Для получения информации о количестве остатков для FBS и rFBS
используйте [/v2/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_GetProductInfoStocksByWarehouseFbsV2).

Чтобы обновить цены по товарам и не менять карточку товара,
используйте [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices).

Метод позволяет обновить цену:

- до скидок,
- для клиентов с подпиской Ozon Premium,
- на карточке товара с учётом скидок,
- минимальную цену товара после применения акций.

Цена товара может упасть ниже минимальной, если вы примените разные типы акций к одному товару.

Для получения информации о ценах, комиссиях и скидках на товары
используйте [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices).

## Резерв товаров

Если товары заказывают юридические лица, оплата может поступать не сразу — система зарезервирует товары.
Чтобы проверить остатки, используйте методы [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3), [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) или [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).
Если в ответе `is_legal = true`, значит среди остатков есть зарезервированные товары.
Вы можете обновить остатки так, чтобы новое количество товаров было больше свободного остатка и зарезервированного товара в сумме. 
Система спишет старый остаток и рассчитает новый.

Чтобы проверить резервирование товара, используйте методы [/v2/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_GetProductInfoStocksByWarehouseFbsV2) или [/v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks).

[Подробнее об изменении остатков](https://seller-edu.ozon.ru/fbs/logistics-settings/upravlenie-ostatkami/#как-меняются-остатки-в-разных-ситуациях)

# Участвуйте в акциях Ozon

Для продвижения товаров участвуйте в акциях, которые Ozon проводит для покупателей.

- Получите список доступных акций: [/v1/actions](#operation/Promos).

- Получите список товаров, которые могут участвовать в акции: [/v1/actions/candidates](#operation/PromosCandidates).

- Добавьте товары в акцию: [/v1/actions/products/activate](#operation/PromosProductsActivate).

- Получите список товаров, которые участвуют в акции: [/v1/actions/products](#operation/PromosProducts).

- Удалите товары из акции: [/v1/actions/products/deactivate](#operation/PromosProductsDeactivate).

Покупатели могут попросить у вас скидку на товар.
Чтобы получить список товаров, которые покупатели хотят купить со скидкой, воспользуйтесь методом
[/v1/actions/discounts-task/list](#operation/promos_task_list).
Заявки в статусах `NEW` (новые) или `SEEN` (просмотренные) вы можете:
- одобрить — используйте метод [/v1/actions/discounts-task/approve](#operation/promos_task_approve),
- отклонить — используйте метод [/v1/actions/discounts-task/decline](#operation/promos_task_decline).

[Подробнее об акциях Ozon в Базе знаний продавца](https://seller-edu.ozon.ru/docs/how-to-sell-effectively/promo/promo.html)

# Работа с акциями продавца

- Создайте акцию:
 - [/v1/seller-actions/create/discount](#operation/SellerActionsCreateDiscount) — с механикой «Скидка»;
 - [/v1/seller-actions/create/discount-with-condition](#operation/SellerActionsCreateDiscountWithCondition) — с механикой «Скидка от суммы заказа»;
 - [/v1/seller-actions/create/installment](#operation/SellerActionsCreateInstallment) — с механикой «Беспроцентная рассрочка»;
 - [/v1/seller-actions/create/multi-level-discount](#operation/SellerActionsCreateMultiLevelDiscount) — с механикой «Многоуровневая скидка от суммы»;
 - [/v1/seller-actions/create/voucher](#operation/SellerActionsCreateVoucher) — с механикой «Скидка по промокоду».
- Отредактируйте акцию:
 - [/v1/seller-actions/update/discount](#operation/SellerActionsUpdateDiscount) — с механикой «Скидка»;
 - [/v1/seller-actions/update/discount-with-condition](#operation/SellerActionsUpdateDiscountWithCondition) — с механикой «Скидка от суммы заказа»;
 - [/v1/seller-actions/update/installment](#operation/SellerActionsUpdateInstallment) — с механикой «Беспроцентная рассрочка»;
 - [/v1/seller-actions/update/multi-level-discount](#operation/SellerActionsUpdateMultiLevelDiscount) — с механикой «Многоуровневая скидка от суммы»;
 - [/v1/seller-actions/update/voucher](#operation/SellerActionsUpdateVoucher) — с механикой «Скидка по промокоду».
- [/v1/seller-actions/list](#operation/SellerActionsList) — получите список созданных акций.
- [/v1/seller-actions/products/candidates](#operation/SellerActionsProductsCandidates) — получите список товаров, которые могут участвовать в акции.
- [/v1/seller-actions/products/add](#operation/SellerActionsProductsAdd) — добавьте товары в акцию.
- [/v1/seller-actions/products/list](#operation/SellerActionsProductsList) — получите список товаров, которые участвуют в акции.
- [/v1/seller-actions/products/delete](#operation/SellerActionsProductsDelete) — удалите товары из акции.
- [/v1/seller-actions/voucher/get](#operation/SellerActionsVoucherGet) — получите список промокодов для акции с механикой «Скидка по промокоду».
- [/v1/seller-actions/change-activity](#operation/SellerActionsChangeActivity) — включите или выключите акцию.
- [/v1/seller-actions/archive](#operation/SellerActionsArchive) — поместите акцию в архив.

[Подробнее об акциях продавца в Базе знаний продавца](https://seller-edu.ozon.ru/libra/ceny-i-akcii/akcii-skidki-i-kupony/akcii-prodavca)

# Настройте стратегии ценообразования

Стратегии ценообразования — инструмент для автоматического изменения стоимости товаров в соответствии с ценами на аналогичные товары в других интернет-магазинах и маркетплейсах.

[Подробнее о стратегиях в Базе знаний для продавцов из России](https://seller-edu.ozon.ru/work-with-goods/rabota-s-tsenami/rival-strategies)

Чтобы настроить стратегии ценообразования:

1. Получите список конкурентов: [/v1/pricing-strategy/competitors/list](#operation/pricing_competitors).

2. Получите список стратегий ценообразования: [/v1/pricing-strategy/list](#operation/pricing_list).

3. Создайте свою стратегию: [/v1/pricing-strategy/create](#operation/pricing_create) и установите коэффициенты, чтобы изменять стоимость товара по сравнению с другими площадками в большую и меньшую сторону.
 Чтобы получить информацию о стратегии, используйте метод [/v1/pricing-strategy/info](#operation/pricing_info).

4. Добавьте товары в стратегию: [/v1/pricing-strategy/products/add](#operation/pricing_items-add).
 
 Вы можете добавить товары:
 - На которые установлена минимальная цена с помощью метода [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices). 
 Чтобы проверить цену, используйте метод [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices).
 - Которые не привязаны к другой стратегии.
 Чтобы проверить привязку товара к стратегии, используйте метод [/v1/pricing-strategy/strategy-ids-by-product-ids](#operation/pricing_ids).

 Чтобы получить список товаров, которые привязаны к стратегии, используйте метод [/v1/pricing-strategy/products/list](#operation/pricing_items-list), а для удаления товаров из стратегии — [/v1/pricing-strategy/products/delete](#operation/pricing_items-delete).

5. Включите или отключите стратегию: [/v1/pricing-strategy/status](#operation/pricing_status).

Чтобы изменить список выбранных конкурентов и название стратегии, используйте метод [/v1/pricing-strategy/update](#operation/pricing_update).

Для удаления стратегии используйте метод [/v1/pricing-strategy/delete](#operation/pricing_delete).

# Получите информацию о складах

- [/v2/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodListV2) — получите список методов rFBS-склада.

- [/v2/warehouse/list](#operation/WarehouseListV2) — получите список складов.

# Работа с FBS-складами

## Создайте новый склад

1. [/v1/warehouse/fbs/create/drop-off/list](#operation/WarehouseAPI_ListDropOffPointsForCreateFBSWarehouse) — получите список drop-off точек и выберите одну, чтобы создать склад.
2. [/v1/warehouse/fbs/return-mile/check](#operation/WarehouseFbsReturnMileCheck) — проверьте необходимость установки возвратной мили. 
3. [/v1/warehouse/fbs/create/return-point/list](#operation/WarehouseFBSCreateReturnPointList) — получите список возвратных пунктов для создания склада.
4. [/v1/warehouse/fbs/create](#operation/WarehouseAPI_CreateWarehouseFBS) — отправьте запрос на создание нового склада.
5. [/v1/warehouse/operation/status](#operation/WarehouseAPI_GetWarehouseFBSOperationStatus) — получите статус операции на создание нового склада.
6. [/v2/warehouse/list](#operation/WarehouseListV2) — получите подробную информацию о складе по `warehouse_id`.

## Обновите настройки склада

1. [/v1/warehouse/fbs/update](#operation/UpdateWarehouseFBS) — отправьте запрос на обновление настроек склада.
2. [/v1/warehouse/operation/status](#operation/WarehouseAPI_GetWarehouseFBSOperationStatus) — получите статус обновления информации о складе.

## Обновите первую милю склада

1. [/v1/warehouse/fbs/return-mile/info](#operation/WarehouseFBSReturnMileInfo) — проверьте необходимость передачи возвратной мили.
2. [/v1/warehouse/fbs/update/return-point/list](#operation/WarehouseFBSUpdateReturnPointList) — получите список пунктов возвратов для обновления склада.
3. [/v1/warehouse/fbs/update/drop-off/list](#operation/WarehouseAPI_ListDropOffPointsForUpdateFBSWarehouse) — получите список drop-off точек и выберите одну, чтобы обновить информацию о складе.
4. [/v1/warehouse/fbs/first-mile/update](#operation/UpdateWarehouseFBSFirstMile) — отправьте запрос на обновление первой мили.
5. [/v1/warehouse/operation/status](#operation/WarehouseAPI_GetWarehouseFBSOperationStatus) — получите статус обновления первой мили.

## Архивируйте склад

1. [/v1/warehouse/fbs/return-mile/info](#operation/WarehouseFBSReturnMileInfo) или [/v1/warehouse/fbs/return-mile/check](#operation/WarehouseFbsReturnMileCheck) — проверьте необходимость установки возвратной мили.
2. [/v1/warehouse/fbs/update/return-point/list](#operation/WarehouseFBSUpdateReturnPointList) — получите список пунктов возвратов для обновления склада.
3. [/v1/warehouse/archive](#operation/WarehouseAPI_ArchiveWarehouseFBS) — перенесите склад в архив.
4. [/v1/warehouse/operation/status](#operation/WarehouseAPI_GetWarehouseFBSOperationStatus) — получите статус архивации склада.

## Уберите склад из архива

1. [/v1/warehouse/fbs/return-mile/info](#operation/WarehouseFBSReturnMileInfo) или [/v1/warehouse/fbs/return-mile/check](#operation/WarehouseFbsReturnMileCheck) — проверьте необходимость установки возвратной мили. 
2. [/v1/warehouse/fbs/update/return-point/list](#operation/WarehouseFBSUpdateReturnPointList) — получите список пунктов возвратов для обновления склада.
3. [/v1/warehouse/unarchive](#operation/WarehouseAPI_UnarchiveWarehouseFBS) — уберите склад из архива.
4. [/v1/warehouse/operation/status](#operation/WarehouseAPI_GetWarehouseFBSOperationStatus) — получите статус разархивации склада.

# Работа со складами rFBS Express

## Доставка «Партнёры Ozon»

### Создайте новый склад

1. [/v1/warehouse/erfbs/aggregator/create](#operation/WarehouseERFBSAggregatorCreate) — создайте новый склад.
2. [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus) — получите статус создания склада по идентификатору операции `operation_id`.
3. [/v1/delivery-method/return/settings/get](#operation/GetDeliveryMethodReturnSettingsV1) — получите информацию по возвратным настройкам.

### Обновите информацию о складе

- [/v1/warehouse/erfbs/update](#operation/WarehouseERFBSUpdate) — обновите информацию о складе.
- [/v1/warehouse/erfbs/aggregator/delivery-method/update](#operation/WarehouseERFBSAggregatorDeliveryMethodUpdate) — обновите информацию о методе доставки.
- [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus) — получите статус изменения информации по идентификатору операции `operation_id`.

## Доставка «Вы или сторонняя служба»

### Создайте новый склад

1. [/v1/warehouse/erfbs/non-integrated/create](#operation/WarehouseERFBSNonIntegratedCreate) — создайте новый склад.
2. [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus) — получите статус создания склада по идентификатору операции `operation_id`.
3. [/v1/delivery-method/return/settings/get](#operation/GetDeliveryMethodReturnSettingsV1) — получите информацию по возвратным настройкам.

### Привяжите полигоны доставки к складу

1. [/v1/polygon/create](#operation/PolygonAPI_CreatePolygon) — создайте полигон доставки.
2. [/v2/polygon/bind](#operation/PolygonBind) — привяжите полигон к методу доставки на складе.

### Обновите информацию о складе

- [/v1/warehouse/erfbs/update](#operation/WarehouseERFBSUpdate) — обновите информацию о складе.
- [/v1/warehouse/erfbs/non-integrated/delivery-method/update](#operation/WarehouseERFBSNonIntegratedDeliveryMethodUpdate) — обновите информацию о методе доставки.
- [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus) — получите статус изменения информации по идентификатору операции `operation_id`.

### Обновите информацию о полигонах доставки

- [/v1/polygon/list](#operation/PolygonList) — получите список полигонов доставки, которые привязаны к складу.
- [/v1/polygon/delete](#operation/PolygonDelete) — удалите полигон из области доставки.
- [/v1/polygon/time/coordinates/update](#operation/PolygonTimeCoordinatesUpdate) — обновите координаты полигона доставки.
- [/v1/polygon/time/set](#operation/PolygonTimeSet) — обновите время доставки в полигоне.

# Управляйте заказами FBO, FBS, rFBS и FBP

Обработайте заказы в зависимости от схемы работы:

- [cхема FBO](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-FBO)
- [стандартная схема FBS](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-FBS-Standart)
- [схема FBS PickUp с подключённой доверительной приёмкой](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-FBS-PickUp-s-doveritelnoj-priyomkoj)
- [Ozon Доставка](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Ozon-Dostavka)
- [стандартная схема rFBS](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-rFBS-Standart)
- [схема rFBS Express с доставкой в пункт выдачи](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-rFBS-Express-s-dostavkoj-v-punkt-vydachi)
- [схема rFBS с доставкой через интегрированную службу](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-rFBS-s-integrirovannoj-sluzhboj-dostavki)
- [схема rFBS Агрегатор](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-rFBS-Agregator)

Если вы продаёте товары из-за рубежа, обрабатывайте заказы по одной из схем:

- [rFBS Crossborder](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-rFBS-Crossborder)
- [rFBS Crossborder с интегрированной службой доставки](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-rFBS-Crossborder-s-integrirovannoj-sluzhboj-dostavki)
- [rFBS Агрегатор](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-rFBS-Agregator)
- [схема FBP](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-FBP)

[Подробнее о заказах с весовыми товарами при работе по схеме rFBS](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Kak-rabotat-s-zakazami-s-vesovymi-tovarami-(rFBS))

## Схема FBO

Перед созданием заявки на поставку проверьте загруженность складов Ozon: [/v1/supplier/available_warehouses](#operation/SupplierAPI_SupplierAvailableWarehouses).

Для получения списка отправлений, финансовой и аналитической информации
используйте [/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList). Также метод возвращает информацию о
проданных кодах активации с привязкой к номеру отправления.

Чтобы получить информацию по отправлению, используйте [/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting).

### Создать заявку на поставку

1. [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList) или [/v2/cluster/list](#operation/DraftClusterList) — получите информацию по кластерам и их складам.
2. Создайте черновик заявки на поставку:
 - [/v1/draft/direct/create](#operation/DraftDirectCreate) — прямую;
 - [/v1/draft/crossdock/create](#operation/DraftCrossdockCreate) — кросс-докингом;
 - [/v1/draft/multi-cluster/create](#operation/DraftMultiClusterCreate) — для нескольких кластеров.

 Если вы выбрали поставку кросс-докингом или в несколько кластеров, укажите схему доставки:
 - Drop-off — заполните параметры `delivery_info.drop_off_warehouse.warehouse_id` и `delivery_info.drop_off_warehouse.warehouse_type`. Получите значения параметров методом [/v1/warehouse/fbo/list](#operation/SupplyDraftAPI_DraftGetWarehouseFboList).
 - Pick-up — заполните параметр `delivery_info.seller_warehouse_id`. Получите значение параметра методом [/v1/warehouse/fbo/seller/list](#operation/WarehouseFboSellerList).
3. [/v2/draft/create/info](#operation/DraftCreateInfo) — получите статус создания черновика и информацию по нему.
4. [/v2/draft/timeslot/info](#operation/DraftTimeslotInfo) — получите доступные таймслоты для конечных складов отгрузки. Максимальный период — 28 дней, начиная с текущей даты.
5. [/v2/draft/supply/create](#operation/DraftSupplyCreate) — создайте заявку на поставку по черновику.
6. [/v2/draft/supply/create/status](#operation/DraftSupplyCreateStatus) — получите статус создания заявки на поставку. Когда заявка будет создана, метод вернёт идентификаторы заявок на поставку.

### Получите информацию о заявках на поставку

Для поставки на фулфилмент Ozon нужна заявка. В ней указано, какие товары и в каком количестве вы привезёте. 

1. [/v3/supply-order/list](#operation/SupplyOrderList) — получите список заявок на поставку.
2. [/v1/supply-order/status/counter](#operation/SupplyOrderAPI_SupplyOrderStatusCounter) — получите статус заявки и количество поставок в этом статусе.
3. [/v3/supply-order/get](#operation/SupplyOrderGet) — получите информацию по заявке.
4. [/v1/supply-order/bundle](#operation/SupplyOrderBundle) — получите состав поставки или заявки на поставку.

Для проезда на фулфилмент выберите интервал поставки и оформите пропуск для водителя и автомобиля. Для этого:

1. [/v1/supply-order/timeslot/get](#operation/SupplyOrderAPI_GetSupplyOrderTimeslots) — получите список доступных интервалов.
2. [/v1/supply-order/timeslot/update](#operation/SupplyOrderAPI_UpdateSupplyOrderTimeslot) — измените выбранный интервал.
3. [/v1/supply-order/timeslot/status](#operation/SupplyOrderAPI_GetSupplyOrderTimeslotStatus) — получите статус закрепления интервала.
4. [/v1/supply-order/pass/create](#operation/SupplyOrderAPI_SupplyOrderPassCreate) — добавьте данные водителя и автомобиля.
5. [/v1/supply-order/pass/status](#operation/SupplyOrderAPI_SupplyOrderPassStatus) — получите статус ввода данных о водителе и автомобиле.

### Управляйте грузоместами в заявке на поставку

1. [/v1/cargoes/create](#operation/CargoesAPI_CargoesCreate) — передайте количество грузомест и установите в каждое грузоместо товарный состав.
2. [/v2/cargoes/get](#operation/CargoesGetV2) — получите информацию о грузоместах.
3. [/v2/cargoes/create/info](#operation/CargoesCreateInfoV2) — получите информацию по установке грузомест и товарного состава.
4. [/v1/cargoes-label/create](#operation/CargoesAPI_CargoesLabelCreate) — создайте задание на формирование этикеток грузомест.
5. [/v1/cargoes-label/get](#operation/CargoesAPI_CargoesLabelGet) — получите статус создания этикеток и идентификатор файла с ними.
6. [/v1/cargoes/rules/get](#operation/CargoesAPI_CargoesRulesGet) — получите чек-лист с правилами по установке грузомест.

### Распределите товары по транспортным грузоместам FBO

1. [/v1/cargoes/transport/activate](#operation/CargoesTransportActivate) — включите транспортные грузоместа в поставке.
2. [/v1/cargoes/transport/activate/status](#operation/CargoesTransportActivateStatus) — получите статус включения транспортных грузомест.
3. [/v1/cargoes/transport/create](#operation/CargoesTransportCreate) — создайте транспортные грузоместа.
4. [/v1/cargoes/transport/create/status](#operation/CargoesTransportCreateStatus) — получите статус создания транспортного грузоместа.
5. [/v2/cargoes/get](#operation/CargoesGetV2) — получите информацию о грузоместах.
6. [/v1/cargoes/create](#operation/CargoesAPI_CargoesCreate) — передайте количество грузомест и установите в каждое грузоместо товарный состав.
7. [/v2/cargoes/create/info](#operation/CargoesCreateInfoV2) — получите информацию об установке грузомест и товарного состава.
8. [/v1/cargoes-label/create](#operation/CargoesAPI_CargoesLabelCreate) — сгенерируйте этикетки для грузомест. Вы можете получать этикетки после создания каждого грузоместа или когда создадите все необходимые грузоместа.
9. [/v1/cargoes-label/get](#operation/CargoesAPI_CargoesLabelGet) — получите статус создания этикеток и идентификатор файла с ними. 
10. [/v1/cargoes/transport/bind](#operation/CargoesTransportBind) — привяжите грузоместа к транспортным грузоместам.
11. [/v1/cargoes/transport/bind/status](#operation/CargoesTransportBindStatus) — получите статус связывания грузомест и транспортных грузомест.
12. [/v1/cargoes/supplies/get](#operation/CargoesSuppliesGet) — получите информацию о грузоместах в поставках. Вы можете проверить полноту загрузки транспортных грузомест и проверить, все ли грузоместа привязаны к транспортным грузоместам. Если привязаны не все, привяжите оставшиеся.

Чтобы удалить грузоместа или транспортные грузоместа, используйте метод [/v2/cargoes/delete](#operation/CargoesDeleteV2). Чтобы получить информацию о статусе их удаления — метод [/v2/cargoes/delete/status](#operation/CargoesDeleteStatusV2).

Чтобы перераспределить грузоместа по транспортным грузоместам, используйте:
1. [/v1/cargoes/supplies/get](#operation/CargoesSuppliesGet) — получите информацию о текущем распределении грузомест в поставках.
2. [/v2/cargoes/get](#operation/CargoesGetV2) — получите информацию о грузоместах.
3. [/v1/cargoes/transport/bind](#operation/CargoesTransportBind) — отвяжите грузоместа от транспортных грузомест.
4. [/v1/cargoes/transport/bind/status](#operation/CargoesTransportBindStatus) — получите статус отвязывания грузомест и транспортных грузомест.
5. [/v1/cargoes/transport/create](#operation/CargoesTransportCreate) — создайте транспортные грузоместа.
6. [/v1/cargoes/transport/create/status](#operation/CargoesTransportCreateStatus) — получите статус создания транспортного грузоместа.
7. [/v1/cargoes/transport/bind](#operation/CargoesTransportBind) — привяжите грузоместа к транспортным грузоместам.
8. [/v1/cargoes/transport/bind/status](#operation/CargoesTransportBindStatus) — получите статус связывания грузомест и транспортных грузомест.

Когда поставка будет полностью укомплектована, получите этикетки транспортных грузомест. Если нужны:
- все этикетки по заявке — используйте [/v1/cargoes/label/transport-by-order/create](#operation/CargoesLabelTransportByOrderCreate), чтобы сгенерировать этикетки для транспортных грузомест по идентификатору поставки, и [/v1/cargoes/label/transport-by-order/status](#operation/CargoesLabelTransportByOrderStatus), чтобы получить статус генерации таких этикеток;
- этикетки для конкретных транспортных грузомест — используйте [/v1/cargoes/label/transport/create](#operation/CargoesLabelTransportCreate), чтобы сгенерировать этикетки транспортных грузомест по идентификатору грузоместа, и [/v1/cargoes/label/transport/status](#operation/CargoesLabelTransportStatus), чтобы получить статус генерации таких этикеток.

Чтобы получить чек-лист с правилами по установке грузомест, используйте [/v1/cargoes/rules/get](#operation/CargoesAPI_CargoesRulesGet).

## Схема FBS Стандарт

1. Перед началом работы с отправлениями получите список необработанных
 отправлений: [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Если покупатель юридическое лицо, то в блоке `requirements` будет информация о необходимости передать
 страну-производителя для всех товаров в заказе, у которых она не указана. Получите список доступных для выбора
 стран: [/v2/posting/fbs/product/country/list](#operation/PostingAPI_ListCountryProductFbsPostingV2). Затем передайте
 информацию о
 стране-производителе: [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).

 Также можно получать список заказов (отправлений): [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3).
 Он позволяет получить все заказы, используя фильтры с различными статусами. Можно также получить данные аналитики,
 если поле `with` отправить со значением `analytics_data`.

 Отправления могут прийти в статусах `awaiting_packaging`, `awaiting_approve` или `awaiting_verification`.

2. Получите дополнительную информацию о заказах: [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3).

 В блоке `requirements` указывается:
 - какие товары подлежат обязательной маркировке;
 - нужно ли передать номер грузовой таможенной декларации и регистрационный номер партии товара — эту информацию
 также можно получить с помощью методов [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)
 и [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Дополнительную информацию вы также можете получить по
 штрихкоду: [/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode).

3. Проверьте, что коды маркировки соответствуют требованиям системы «Честный ЗНАК» по составу и количеству
 символов: [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5).

 Получите идентификаторы экземпляров `exemplar_id` методом [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6).

 С помощью метода [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) добавьте для каждого экземпляра маркировку, которую будете передавать в систему «Честный ЗНАК». При необходимости передайте
 номера таможенных деклараций и регистрационные номера партии товара или укажите, что их нет.
 
 [Подробнее о маркировке «Честный ЗНАК» в Базе знаний](https://seller-edu.ozon.ru/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/obyazatelnaya-markirovka-tovarov)
 
 Получите статусы передачи маркировок:

- [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) — получить статус добавления экземпляров.
- [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) — получить данные созданных экземпляров.

4. Перед сборкой убедитесь, что отправление соответствует установленным в пункте приёма ограничениям. Получите
 ограничения пункта приёма по номеру
 отправления: [/v1/posting/fbs/restrictions](#operation/PostingAPI_GetRestrictions).

5. До окончания времени на сборку подтвердите, что вы собрали
 заказ: [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4). Вы не сможете собрать заказ, если:
 - заказ не в статусе `awaiting_packaging`;
 - вы не указали коды маркировки для товаров, подлежащих обязательной маркировке.

 При необходимости используйте этот метод, чтобы разделить заказ на несколько отправлений. Например, если в заказе
 несколько товаров и их необходимо упаковать в разные коробки, так как вместе они не отвечают требованиям к упаковке.

 После использования метода статус отправления изменится на `awaiting_deliver`.

 Вы можете использовать метод для частичной
 сборки: [/v4/posting/fbs/ship/package](#operation/PostingAPI_ShipFbsPostingPackage).

6. Для каждого отправления распечатайте наклейку для идентификации в системе
 Ozon: [/v2/posting/fbs/package-label](#operation/PostingAPI_PostingFBSPackageLabel).

7. Подтвердите отгрузку и запустите формирование транспортной накладной методом [/v2/posting/fbs/act/create](#operation/PostingAPI_PostingFBSActCreate) или создайте отгрузку с помощью метода [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate) и подтвердите её методом [/v1/carriage/approve](#operation/CarriageAPI_CarriageApprove). 
 В ответе методов [/v2/posting/fbs/act/create](#operation/PostingAPI_PostingFBSActCreate) и [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate) вы получите идентификатор созданной перевозки.

8. Запросите информацию о созданной поставке с помощью метода [/v1/carriage/get](#operation/CarriageGet). 
 Массив `available_actions` содержит информацию о доступных действиях с поставкой и необходимости создать пропуск для проезда на склад Ozon.

 Чтобы создать пропуск, используйте метод [/v1/carriage/pass/create](#operation/carriagePassCreate). 
 Чтобы после поставки товаров вы могли забрать возвраты на этой же машине, передайте значение `with_returns = true`.
 Для каждой поставки нужен новый пропуск.

 Для редактирования или удаления пропуска используйте методы [/v1/carriage/pass/update](#operation/carriagePassUpdate) и [/v1/carriage/pass/delete](#operation/carriagePassDelete).

 Список всех пропусков можно получить с помощью метода [/v1/pass/list](#operation/PassList).

 [Подробнее об оформлении пропусков](https://seller-edu.ozon.ru/fbs/ozon-logistika/oformlenie-propuska)

9. Получите список перевозок, по которым нужно распечатать штрихкод для отгрузки и транспортную накладную: [/v1/posting/carriage-available/list](#operation/PostingAPI_GetCarriageAvailableList) или [/v2/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryListV2).

10. Проверьте, что отгрузка создана: [/v2/posting/fbs/act/check-status](#operation/PostingAPI_PostingFBSActCheckStatus).

11. Получите штрихкод для отгрузки: [/v2/posting/fbs/act/get-barcode](#operation/PostingAPI_PostingFBSGetBarcode).

12. Получите PDF-документы: [/v2/posting/fbs/act/get-pdf](#operation/PostingAPI_PostingFBSGetAct) и [/v1/carriage/act-discrepancy/pdf](#operation/CarriageActDiscrepancyPDF).

После этого можете отвезти отправления и документы в пункт приёма.

Если отправление передано в доставку, но не просканировано в сортировочном центре, вы можете открыть
спор: [/v2/posting/fbs/arbitration](#operation/PostingAPI_MoveFbsPostingToArbitration). Открытый спор переведёт
отправление в статус `arbitration`.

Если спор по отправлению откроет покупатель, статус отправления изменится на `client_arbitration`.

Чтобы отследить изменение статуса, когда отправление найдено,
используйте [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) с нужными фильтрами.

Для передачи спорных заказов к отгрузке
используйте [/v2/posting/fbs/awaiting-delivery](#operation/PostingAPI_MoveFbsPostingToAwaitingDelivery). Статус
отправления изменится на `awaiting_deliver`.

### Отменить доставку отправления

1. Используйте [/v2/posting/fbs/cancel-reason/list](#operation/PostingAPI_GetPostingFbsCancelReasonList) на любом этапе
 работы с отправлением, чтобы получить список причин отмены отправления.

2. Передайте этот список и номер отправления: [/v2/posting/fbs/cancel](#operation/PostingAPI_CancelFbsPosting).

Чтобы отменить часть товаров в отправлении,
используйте [/v2/posting/fbs/product/cancel](#operation/PostingAPI_CancelFbsPostingProduct).

Если отправление отменит покупатель, статус изменится на `cancelled`.

## Схема FBS с электронными ТТН

### Работа с отправлениями

1. Получите список необработанных отправлений: [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) или [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList). 
 В ответе проверьте:
 - `is_blr_traceable` — признак прослеживаемости товара;
 - `require_blr_traceable_attrs = true` — если нужно заполнить атрибуты прослеживаемости;
 - `split_before_ship = true` — если нужно разделить заказ.
 
2. Отфильтруйте прослеживаемые отправления, используя фильтр `is_blr_traceable = true`: [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3).

3. Если заказ с прослеживаемостью, разделите его: [/v1/posting/fbs/traceable/split](#operation/PostingFbsTraceableSplit).

4. Проверьте, нужно ли заполнять атрибуты прослеживаемости: [/v1/posting/fbs/product/traceable/attribute](#operation/PostingFbsProductTraceableAttribute).

5. Если атрибуты нужны, укажите их для карточки товара в личном кабинете или через API:
 - количество товара в УЕИ;
 - штрихкод GTIN.

6. Передайте экземпляры товара и соберите отправление: [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4).

### Работа с перевозками

1. Получите список нулевых отгрузок: [/v2/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryListV2). Прослеживаемые отгрузки будут иметь признак `all_blr_traceable`.

2. Создайте перевозку с прослеживаемыми товарами: [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate). В запросе укажите `is_blr_traceable = true`.
 
 Если точка отгрузки не поддерживает электронную ТТН, вернётся ошибка `BLR_TRACEABLE_PICKUP_NOT_ALLOWED`.

3. Получите информацию о созданной перевозке: [/v1/carriage/get](#operation/CarriageGet). В ответе получите признак `all_blr_traceable`.

4. Создайте и загрузите на проверку электронную ТТН через систему электронного документооборота — ЭДО.

5. Получите статус электронной ТТН: [/v1/carriage/ettn/status](#operation/CarriageEttnStatus).

6. Подтвердите перевозку: [/v1/carriage/approve](#operation/CarriageAPI_CarriageApprove). Если электронная ТТН не прошла проверку, вернётся ошибка `INCORRECT_E_WAYBILL_STATUS`.

7. Обновите товарный состав перевозки, если нужно: [/v1/carriage/set-postings](#operation/CarriageAPI_SetPostings). Если электронная ТТН не прошла проверку, вернётся ошибка `INCORRECT_E_WAYBILL_STATUS`.

## Схема FBS PickUp с доверительной приёмкой

1. Перед началом работы с отправлениями получите список необработанных
 отправлений: [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Если покупатель юридическое лицо, то в блоке `requirements` будет информация о необходимости передать
 страну-производителя для всех товаров в заказе, у которых она не указана. Получите список доступных для выбора
 стран: [/v2/posting/fbs/product/country/list](#operation/PostingAPI_ListCountryProductFbsPostingV2). Затем передайте
 информацию о
 стране-производителе: [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).

 Также можно получать список заказов (отправлений): [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3).
 Он позволяет получить все заказы, используя фильтры с различными статусами. Можно также получить данные аналитики,
 если поле `with` отправить со значением `analytics_data`.

 Отправления могут прийти в статусах `awaiting_packaging`, `awaiting_approve` или `awaiting_verification`.

2. Получите дополнительную информацию о заказах: [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3).

 В блоке `requirements` указывается:
 - какие товары подлежат обязательной маркировке;
 - нужно ли передать номер грузовой таможенной декларации и регистрационный номер партии товара — эту информацию
 также можно получить с помощью методов [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) и
 [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Дополнительную информацию вы также можете получить по
 штрихкоду: [/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode).

3. Проверьте, что коды маркировки соответствуют требованиям системы «Честный ЗНАК» по составу и количеству
 символов: [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5).

 С помощью метода [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) добавьте для каждого экземпляра маркировку, которую будете передавать в систему «Честный ЗНАК». При необходимости передайте
 номера таможенных деклараций и регистрационные номера партии товара или укажите, что их нет.

 [Подробнее о маркировке «Честный ЗНАК» в Базе знаний](https://seller-edu.ozon.ru/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/obyazatelnaya-markirovka-tovarov)

 Получите статусы передачи маркировок:

- [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) — получить статус добавления экземпляров.
- [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) — получить данные созданных экземпляров.

4. Перед сборкой убедитесь, что отправление соответствует установленным в пункте приёма ограничениям. Получите
 ограничения пункта приёма по номеру
 отправления: [/v1/posting/fbs/restrictions](#operation/PostingAPI_GetRestrictions).

5. До окончания времени на сборку подтвердите, что вы собрали
 заказ: [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4). Вы не сможете собрать заказ, если:
 - заказ не в статусе `awaiting_packaging`;
 - вы не указали коды маркировки для товаров, подлежащих обязательной маркировке.

 При необходимости используйте этот метод, чтобы разделить заказ на несколько отправлений. Например, если в заказе
 несколько товаров и их необходимо упаковать в разные коробки, так как вместе они не отвечают требованиям к упаковке.

 После использования метода статус отправления изменится на `awaiting_deliver`.

 Вы можете использовать метод для частичной
 сборки: [/v4/posting/fbs/ship/package](#operation/PostingAPI_ShipFbsPostingPackage).

6. Подтвердите отгрузку и запустите формирование транспортной накладной методом [/v2/posting/fbs/act/create](#operation/PostingAPI_PostingFBSActCreate) или создайте перевозку с помощью метода [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate) и подтвердите её методом [/v1/carriage/approve](#operation/CarriageAPI_CarriageApprove).
 В ответе методов [/v2/posting/fbs/act/create](#operation/PostingAPI_PostingFBSActCreate) и [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate) вы получите идентификатор созданной перевозки.

7. Получите список перевозок, по которым нужно распечатать штрихкод для отгрузки и транспортную накладную: [/v1/posting/carriage-available/list](#operation/PostingAPI_GetCarriageAvailableList) или [/v2/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryListV2).

8. Получите PDF-документы: [/v2/posting/fbs/act/get-pdf](#operation/PostingAPI_PostingFBSGetAct) и [/v1/carriage/act-discrepancy/pdf](#operation/CarriageActDiscrepancyPDF).

9. Для каждого отправления распечатайте наклейку для идентификации в системе
 Ozon: [/v2/posting/fbs/package-label](#operation/PostingAPI_PostingFBSPackageLabel).

10. После того как вы упаковали все отправления по требованиям из
 раздела [Доверительная приёмка грузового места](https://seller-edu.ozon.ru/docs/fbs/ozon-logistika/doveritel-naya-priemka-gruzovogo-mesta.html#какие-требования-к-грузовому-месту)
 в Базе знаний продавца, получите этикетки на каждое грузовое
 место: [/v2/posting/fbs/act/get-container-labels](#operation/PostingAPI_PostingFBSActGetContainerLabels).

После этого можете передать грузовое место в пункт приёма или курьеру Ozon.

Если отправление передано в доставку, но не просканировано в сортировочном центре, вы можете открыть
спор: [/v2/posting/fbs/arbitration](#operation/PostingAPI_MoveFbsPostingToArbitration). Открытый спор переведёт
отправление в статус `arbitration`.

Если спор по отправлению откроет покупатель, статус отправления изменится на `client_arbitration`.

Чтобы отследить изменение статуса, когда отправление найдено,
используйте [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) с нужными фильтрами.

Для передачи спорных заказов к отгрузке
используйте [/v2/posting/fbs/awaiting-delivery](#operation/PostingAPI_MoveFbsPostingToAwaitingDelivery). Статус
отправления изменится на `awaiting_deliver`.

## Ozon Доставка

### Доставка

1. [v1/delivery/check](#operation/DeliveryCheck) — проверьте, может ли покупатель получить заказ через Ozon. Способы доставки для Ozon Доставки:
 - Самовывоз или pickup — покупатель сам забирает товар из точки выдачи заказов.
 - Курьерская или courier — курьер Ozon доставляет товар по выбранному адресу.

 Если способ доставки — самовывоз, передайте идентификатор точки самовывоза в параметр `pickup`.
 При курьерской доставке передайте адрес получения и координаты в параметр `courier`.

2. [v1/delivery/map](#operation/DeliveryMap) — укажите точки на карте, из которых покупатель может забрать заказ.
3. [v1/delivery/point/list](#operation/DeliveryAPI_DeliveryPointList) — получите список точек самовывоза.
4. [/v1/delivery/point/info](#operation/DeliveryPointInfo) — получите информацию о точке самовывоза.
5. [/v2/delivery/checkout](#operation/DeliveryCheckout) — проверьте доступность товара и сроки доставки.

Предоставьте выбор способа доставки и точки доставки на этапе оформления заказа или в корзине. 
Если это невозможно, кешируйте данные на своей стороне, чтобы снизить нагрузку и оптимизировать количество запросов к API.

### Обработка заказа

Создавайте заказ в системе Ozon только после того, как покупатель оплатил его.

1. [v2/order/create](#operation/OrderAPI_OrderCreate) — создайте заказ и начните сборку. После вызова метода изменить заказ не получится.
2. [v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList) и [v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) — отследите все отправления или конкретное.
3. [v1/posting/marks](#operation/PostingAPI_PostingMarks) — получите маркировки экземпляров из отправления. Передавайте в этот метод только отправления, которые вы создали через методы Ozon Доставки.

### Отслеживание отправлений

Для схемы FBO:
- [v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList) — получите список всех отправлений.
- [v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting) — получите информацию о конкретном отправлении.

Для схемы FBS:
- [v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) — получите список необработанных отправлений.
- [v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) — получите список отправлений.
- [v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) — получите информацию об отправлении.

Если покупатель при получении отправления отказался от одного из товаров, отправление останется в статусе «Доставлено». Используйте [v1/returns/list](#operation/returnsList), чтобы получить информацию по возврату с невыкупленным товаром. Тип такого возврата — `type: PartialReturn`.

### Отмена заказа или отправления

Можно отменить заказы, которые создали с помощью методов Ozon Доставки, если:
- Ozon отменил заказ до поступления в пункт выдачи или перед доставкой покупателю.
- Покупатель не забрал заказ при получении — полностью или частично.
- Покупатель запросил отмену заказа через сайт или приложение продавца. Покупатель не может отменить заказ через личный кабинет Ozon.

Возвращайте деньги покупателю только после подтверждения отмены.

Для отмены заказа или его части:
- [/v1/cancel-reason/list-by-order](#operation/CancelReasonListByOrder) — получите возможные причины отмены заказа.
- [/v1/cancel-reason/list-by-posting](#operation/CancelReasonAPI_CancelReasonListByPosting) — получите список доступных причин отмены отправления. Используйте метод, только если покупатель запросил отмену заказа.
- [v1/order/cancel/check](#operation/OrderAPI_OrderCancelCheck) — проверьте, можно ли отменить заказ.
- [v1/order/cancel](#operation/OrderAPI_OrderCancel) — отмените заказ.
- [v1/posting/cancel](#operation/PostingAPI_PostingCancel) — отмените отправление из заказа.
- [v1/order/cancel/status](#operation/OrderAPI_OrderCancelStatus) — проверьте статус отмены заказа.
- [v1/posting/cancel/status](#operation/PostingAPI_PostingCancelStatus) — проверьте статус отмены отправления.

Для отмены FBS-отправлений:
- [v2/posting/fbs/product/cancel](#operation/PostingAPI_CancelFbsPostingProduct) — отмените отправку некоторых товаров в отправлении.
- [v2/posting/fbs/cancel](#operation/PostingAPI_CancelFbsPosting) — отмените отправление.

### Возврат товара

[v1/returns/list](#operation/returnsList) — отследите статус возврата товара.
Используйте, если покупатель отменил заказ во время перевозки или не забрал его при получении. Возвраты от покупателей продавец забирает своими силами.
Если покупатель забрал товар и после этого решил его вернуть, он должен связаться с продавцом.

Если покупатель отказался от одного из товаров при получении отправления, оно останется в статусе «Доставлено». Система создаст новое отправление в статусе «Отменено» с типом отмены `PartialRefund`. Получите информацию о нём методом [v1/returns/list](#operation/returnsList).

### Остатки

- [v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) — получите отчёт по остаткам на складах Ozon, чтобы планировать поставки товаров.
- [v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks) — покажите покупателю количество товаров на складах Ozon.

Если на складах Ozon недостаточно товаров, создать заказ через методы Ozon Доставки не получится.

## Схема rFBS Стандарт

С 11 марта 2024 года максимальный срок доставки до покупателя — 30 дней.
Обновите срок в настройках вашего метода. 
Если срок будет больше максимального, он поменяется автоматически.

1. Перед началом работы с отправлениями получите список необработанных заказов (отправлений):
 [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Если покупатель юридическое лицо, то в блоке `requirements` будет информация о необходимости передать
 страну-производителя для всех товаров в заказе, у которых она не указана. 
 Получите список доступных для выбора
 стран: [/v2/posting/fbs/product/country/list](#operation/PostingAPI_ListCountryProductFbsPostingV2). Затем передайте
 информацию о
 стране-производителе: [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).

 Также можно получать список заказов (отправлений): [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3).
 Он позволяет получить все заказы, используя фильтры с различными статусами. Можно также получить данные аналитики,
 если поле `with` отправить со значением `analytics_data`.

 Отправления могут прийти в статусах `awaiting_packaging`, `awaiting_approve` или `awaiting_verification`.

 Если в параметре `available_actions` указано `set_cutoff`, уточните дату отгрузки отправления с помощью метода
 [/v1/posting/cutoff/set](#operation/PostingAPI_SetPostingCutoff). Сделайте это не позднее даты, которая указана в
 параметре `shipment_date` в методах: [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList),
 [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) или [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3).
 После даты `shipment_date` уточнить дату отгрузки и собрать отправление не получится.

2. Получите дополнительную информацию о заказах: [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3).

 В блоке `requirements` указывается:
 - какие товары подлежат обязательной маркировке;
 - нужно ли передать номер грузовой таможенной декларации и регистрационный номер партии товара — эту информацию
 также можно получить с помощью методов [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)
 и [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Если вы продаёте весовые товары, и в параметре `result.products.is_weight_needed` для товара указано `true`, передайте информацию о весе товара методом [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).

 Дополнительную информацию вы также можете получить по
 штрихкоду: [/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode).

3. Проверьте, что коды маркировки соответствуют требованиям системы «Честный ЗНАК» по составу и количеству
 символов: [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5).

 С помощью метода [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) добавьте для каждого экземпляра маркировку, которую будете передавать в систему «Честный ЗНАК». При необходимости передайте
 номера таможенных деклараций и регистрационные номера партии товара или укажите, что их нет.

 [Подробнее о маркировке «Честный ЗНАК» в Базе знаний](https://seller-edu.ozon.ru/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/obyazatelnaya-markirovka-tovarov)

 Получите статусы передачи маркировок: 

- [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) — получить статус добавления экземпляров.
- [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) — получить данные созданных экземпляров.

4. До окончания времени на сборку подтвердите, что вы собрали
 заказ: [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4). Вы не сможете собрать заказ, если:
 - заказ не в статусе `awaiting_packaging`;
 - вы не указали коды маркировки для товаров, подлежащих обязательной маркировке.

 При необходимости используйте этот метод, чтобы разделить заказ на несколько отправлений. Например, если в заказе
 несколько товаров и их необходимо упаковать в разные коробки, так как вместе они не отвечают требованиям к упаковке.

 После использования метода статус отправления изменится на `awaiting_deliver`.

 Вы можете использовать метод для частичной
 сборки: [/v4/posting/fbs/ship/package](#operation/PostingAPI_ShipFbsPostingPackage).

Когда сборка заказа завершена, свяжитесь с покупателем для согласования даты доставки.
Если покупателю не подходит дата, вы можете перенести её: [/v1/posting/fbs/timeslot/set](#operation/PostingAPI_SetPostingTimeslot).
Посмотрите доступные даты для переноса доставки и количество доступных переносов: [/v1/posting/fbs/timeslot/change-restrictions](#operation/PostingAPI_PostingTimeslotChangeRestrictions).

Передайте отправление курьеру:

1. Когда курьер забрал отправление, измените статус отправления на
 «Доставляется»: [/v2/fbs/posting/delivering](#operation/PostingAPI_FbsPostingDelivering).

 
 Если вы не составляете маршрутный лист и курьер сразу направляется к покупателю, можете сразу перевести отправление из
 статуса «Доставляется» в «Последняя миля»: [/v2/fbs/posting/last-mile](#operation/PostingAPI_FbsPostingLastMile).
 

 Одновременно с этим, если у отправления есть трек-номер, передайте
 его: [/v2/fbs/posting/tracking-number/set](#operation/PostingAPI_FbsPostingTrackingNumberSet).

2. Когда курьер едет к покупателю, поменяйте статус отправления на «Последняя
 миля»: [/v2/fbs/posting/last-mile](#operation/PostingAPI_FbsPostingLastMile).

3. Когда курьер передал отправление покупателю, поменяйте статус на
 «Доставлено»: [/v2/fbs/posting/delivered](#operation/PostingAPI_FbsPostingDelivered).

### Отменить доставку отправления

1. Используйте [/v2/posting/fbs/cancel-reason/list](#operation/PostingAPI_GetPostingFbsCancelReasonList) на любом этапе
 работы с отправлением, чтобы получить список причин отмены отправления.

2. Передайте этот список и номер отправления: [/v2/posting/fbs/cancel](#operation/PostingAPI_CancelFbsPosting).

Чтобы отменить часть товаров в отправлении,
используйте [/v2/posting/fbs/product/cancel](#operation/PostingAPI_CancelFbsPostingProduct).

Если отправление отменит покупатель, статус изменится на `cancelled`.

## Схема rFBS Express с доставкой в пункт выдачи

1. Перед началом работы с отправлениями получите список необработанных заказов (отправлений):
 [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Если покупатель юридическое лицо, то в блоке `requirements` будет информация о необходимости передать страну-производителя для всех товаров в заказе, у которых она не указана.
 Получите список доступных для выбора стран: [/v2/posting/fbs/product/country/list](#operation/PostingAPI_ListCountryProductFbsPostingV2). 
 Затем передайте информацию о стране-производителе: [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).

 Также можно получать список заказов (отправлений): [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3).
 Он позволяет получить все заказы, используя фильтры с различными статусами. 
 Можно также получить данные аналитики, если поле `with` отправить со значением `analytics_data`.

 Отправления могут прийти в статусах `awaiting_packaging`, `awaiting_approve` или `awaiting_verification`.

2. Получите дополнительную информацию о заказах: [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3).

 В блоке `requirements` указывается:
 - какие товары подлежат обязательной маркировке;
 - нужно ли передать номер грузовой таможенной декларации и регистрационный номер партии товара — эту информацию
 также можно получить с помощью методов [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) и [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Дополнительную информацию вы также можете получить по штрихкоду: [/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode).

3. Проверьте, что коды маркировки соответствуют требованиям системы «Честный ЗНАК» по составу и количеству
 символов: [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5).

 С помощью метода [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) добавьте для каждого экземпляра маркировку, которую будете передавать в систему «Честный ЗНАК». 
 При необходимости передайте номера таможенных деклараций и регистрационные номера партии товара или укажите, что их нет.

 [Подробнее о маркировке «Честный ЗНАК» в Базе знаний](https://seller-edu.ozon.ru/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/obyazatelnaya-markirovka-tovarov)

 Получите статусы передачи маркировок:

- [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) — получить статус добавления экземпляров.
- [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) — получить данные созданных экземпляров.

4. До окончания времени на сборку подтвердите, что вы собрали заказ: [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4). 
 Вы не сможете собрать заказ, если:
 - заказ не в статусе `awaiting_packaging`;
 - вы не указали коды маркировки для товаров, подлежащих обязательной маркировке.

 При необходимости используйте этот метод, чтобы разделить заказ на несколько отправлений. 
 Например, если в заказе несколько товаров и их необходимо упаковать в разные коробки, так как вместе они не отвечают требованиям к упаковке.

 После использования метода статус отправления изменится на `awaiting_deliver`.

 Вы можете использовать метод для частичной сборки: [/v4/posting/fbs/ship/package](#operation/PostingAPI_ShipFbsPostingPackage).

5. Распечатайте этикетку для идентификации в системе Ozon: [/v2/posting/fbs/package-label](#operation/PostingAPI_PostingFBSPackageLabel). 

6. Передайте отправление курьеру.

Дальше подстатусы будут изменяться автоматически: 
1. `on_way_to_city` — курьер забрал заказ. 
2. `on_way_to_pickup_point` — курьер везёт заказ в пункт выдачи.
3. `in_pickup_point` — отправление приняли в пункте выдачи.
4. `delivered` — покупатель забрал заказ из пункта выдачи.

Чтобы проверить статус отправления, используйте метод [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3).

### Отменить доставку отправления

1. Используйте [/v2/posting/fbs/cancel-reason/list](#operation/PostingAPI_GetPostingFbsCancelReasonList) на любом этапе
 работы с отправлением, чтобы получить список причин отмены отправления.

2. Передайте этот список и номер отправления: [/v2/posting/fbs/cancel](#operation/PostingAPI_CancelFbsPosting).

Чтобы отменить часть товаров в отправлении, используйте [/v2/posting/fbs/product/cancel](#operation/PostingAPI_CancelFbsPostingProduct).

Если отправление отменит покупатель, статус изменится на `cancelled`.

## Схема rFBS с интегрированной службой доставки

1. Перед началом работы с отправлениями получите список необработанных заказов (отправлений):
 [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Если покупатель юридическое лицо, то в блоке `requirements` будет информация о необходимости передать
 страну-производителя для всех товаров в заказе, у которых она не указана. Получите список доступных для выбора
 стран: [/v2/posting/fbs/product/country/list](#operation/PostingAPI_ListCountryProductFbsPostingV2). Затем передайте
 информацию о
 стране-производителе: [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).

 Также можно получать список заказов (отправлений): [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3).
 Он позволяет получить все заказы, используя фильтры с различными статусами. Можно также получить данные аналитики,
 если поле `with` отправить со значением `analytics_data`.

 Отправления могут прийти в статусах `awaiting_packaging`, `awaiting_approve` или `awaiting_verification`.

2. Получите дополнительную информацию о заказах: [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3).

 В блоке `requirements` указывается:
 - какие товары подлежат обязательной маркировке;
 - нужно ли передать номер грузовой таможенной декларации и регистрационный номер партии товара — эту информацию
 также можно получить с помощью методов [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)
 и [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Дополнительную информацию вы также можете получить по
 штрихкоду: [/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode).

3. Проверьте, что коды маркировки соответствуют требованиям системы «Честный ЗНАК» по составу и количеству
 символов: [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5).

 С помощью метода [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) добавьте для каждого экземпляра маркировку, которую будете передавать в систему «Честный ЗНАК». При необходимости передайте
 номера таможенных деклараций и регистрационные номера партии товара или укажите, что их нет.

 [Подробнее о маркировке «Честный ЗНАК» в Базе знаний](https://seller-edu.ozon.ru/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/obyazatelnaya-markirovka-tovarov)

 Получите статусы передачи маркировок:

- [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) — получить статус добавления экземпляров.
- [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) — получить данные созданных экземпляров.

4. До окончания времени на сборку подтвердите, что вы собрали
 заказ: [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4). Вы не сможете собрать заказ, если:
 - заказ не в статусе `awaiting_packaging`;
 - вы не указали коды маркировки для товаров, подлежащих обязательной маркировке.

 При необходимости используйте этот метод, чтобы разделить заказ на несколько отправлений. Например, если в заказе
 несколько товаров и их необходимо упаковать в разные коробки, так как вместе они не отвечают требованиям к упаковке.

 После использования метода статус отправления изменится на `awaiting_deliver`.

 Вы можете использовать метод для частичной
 сборки: [/v4/posting/fbs/ship/package](#operation/PostingAPI_ShipFbsPostingPackage).

Передайте отправление в службу доставки. Все статусы от «Доставляется» до «Доставлено» будет передавать служба доставки.

### Отменить доставку отправления

1. Используйте [/v2/posting/fbs/cancel-reason/list](#operation/PostingAPI_GetPostingFbsCancelReasonList) на любом этапе
 работы с отправлением, чтобы получить список причин отмены отправления.

2. Передайте этот список и номер отправления: [/v2/posting/fbs/cancel](#operation/PostingAPI_CancelFbsPosting).

Чтобы отменить часть товаров в отправлении,
используйте [/v2/posting/fbs/product/cancel](#operation/PostingAPI_CancelFbsPostingProduct).

Если отправление отменит покупатель, статус изменится на `cancelled`.

## Схема rFBS Агрегатор

1. Перед началом работы с отправлениями получите список необработанных заказов (отправлений):
 [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Если покупатель юридическое лицо, то в блоке `requirements` будет информация о необходимости передать
 страну-производителя для всех товаров в заказе, у которых она не указана. Получите список доступных для выбора
 стран: [/v2/posting/fbs/product/country/list](#operation/PostingAPI_ListCountryProductFbsPostingV2). Затем передайте
 информацию о
 стране-производителе: [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).

 Также можно получать список заказов (отправлений): [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3).
 Он позволяет получить все заказы, используя фильтры с различными статусами. Можно также получить данные аналитики,
 если поле `with` отправить со значением `analytics_data`.

 Отправления могут прийти в статусах `awaiting_packaging`, `awaiting_approve` или `awaiting_verification`.

2. Получите дополнительную информацию о заказах: [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3).

 В блоке `requirements` указывается:
 - какие товары подлежат обязательной маркировке;
 - нужно ли передать номер грузовой таможенной декларации и регистрационный номер партии товара — эту информацию
 также можно получить с помощью методов [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)
 и [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Дополнительную информацию вы также можете получить по
 штрихкоду: [/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode).

3. Проверьте, что коды маркировки соответствуют требованиям системы «Честный ЗНАК» по составу и количеству
 символов: [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5).

 С помощью метода [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) добавьте для каждого экземпляра маркировку, которую будете передавать в систему «Честный ЗНАК». При необходимости передайте
 номера таможенных деклараций и регистрационные номера партии товара или укажите, что их нет.

 [Подробнее о маркировке «Честный ЗНАК» в Базе знаний](https://seller-edu.ozon.ru/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/obyazatelnaya-markirovka-tovarov)

 Получите статусы передачи маркировок:

- [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) — получить статус добавления экземпляров.
- [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) — получить данные созданных экземпляров.

4. Если товар в отправлении упакован в несколько коробок, передайте их количество: [/v3/posting/multiboxqty/set](#operation/PostingAPI_PostingMultiBoxQtySetV3). Если не сделать этого до сборки, вам придётся объединить все коробки в одну.

5. До окончания времени на сборку подтвердите, что вы собрали
 заказ: [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4). Вы не сможете собрать заказ, если:
 - заказ не в статусе `awaiting_packaging`;
 - вы не указали коды маркировки для товаров, подлежащих обязательной маркировке.

 При необходимости используйте этот метод, чтобы разделить заказ на несколько отправлений. Например, если в заказе
 несколько товаров и их необходимо упаковать в разные коробки, так как вместе они не отвечают требованиям к упаковке.

 После использования метода статус отправления изменится на `awaiting_registration`.

 Вы можете использовать метод для частичной
 сборки: [/v4/posting/fbs/ship/package](#operation/PostingAPI_ShipFbsPostingPackage).

6. Когда перевозчик обработает отправление, его статус изменится с `awaiting_registration` на `awaiting_delivery`. После
 этого отправлению будет присвоен трек-номер.

 Для каждого отправления распечатайте этикетку для идентификации в системе
 Ozon: [/v2/posting/fbs/package-label](#operation/PostingAPI_PostingFBSPackageLabel).

 Передайте отправление в службу доставки. Все статусы от «Доставляется» до «Доставлено» будет передавать служба доставки.

Если вы продаёте из Турции и вам нужны декларации Elektronik Ticaret Gümrük Beyannamesi (ETGB) для возврата налоговой пошлины, 
получите декларации: [/v1/posting/global/etgb](#operation/PostingAPI_GetEtgb).

### Отменить доставку отправления

1. Используйте [/v2/posting/fbs/cancel-reason/list](#operation/PostingAPI_GetPostingFbsCancelReasonList) на любом этапе
 работы с отправлением, чтобы получить список причин отмены отправления.

2. Передайте этот список и номер отправления: [/v2/posting/fbs/cancel](#operation/PostingAPI_CancelFbsPosting).

Чтобы отменить часть товаров в отправлении,
используйте [/v2/posting/fbs/product/cancel](#operation/PostingAPI_CancelFbsPostingProduct).

Если отправление отменит покупатель, статус изменится на `cancelled`.

## Схема rFBS Crossborder

1. Перед началом работы с отправлениями получите список необработанных заказов (отправлений):
 [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Если покупатель юридическое лицо, то в блоке `requirements` будет информация о необходимости передать
 страну-производителя для всех товаров в заказе, у которых она не указана. 
 Получите список доступных для выбора
 стран: [/v2/posting/fbs/product/country/list](#operation/PostingAPI_ListCountryProductFbsPostingV2). Затем передайте
 информацию о
 стране-производителе: [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).

 Также можно получать список заказов (отправлений): [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3).
 Он позволяет получить все заказы, используя фильтры с различными статусами. Можно также получить данные аналитики,
 если поле `with` отправить со значением `analytics_data`.

 Отправления могут прийти в статусах `awaiting_packaging`, `awaiting_approve` или `awaiting_verification`.

 Если в параметре `available_actions` указано `set_cutoff`, уточните дату отгрузки отправления с помощью метода
 [/v1/posting/cutoff/set](#operation/PostingAPI_SetPostingCutoff). Сделайте это не позднее даты, которая указана в
 параметре `shipment_date` в методах: [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList),
 [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) или [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3).
 После даты `shipment_date` уточнить дату отгрузки и собрать отправление не получится.

2. Получите дополнительную информацию о заказах: [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3).

 В блоке `requirements` указывается:
 - какие товары подлежат обязательной маркировке;
 - нужно ли передать номер грузовой таможенной декларации и регистрационный номер партии товара — эту информацию
 также можно получить с помощью методов [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)
 и [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Дополнительную информацию вы также можете получить по
 штрихкоду: [/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode).

3. Проверьте, что коды маркировки соответствуют требованиям системы «Честный ЗНАК» по составу и количеству
 символов: [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5).

 С помощью метода [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) добавьте для каждого экземпляра маркировку, которую будете передавать в систему «Честный ЗНАК». При необходимости передайте
 номера таможенных деклараций и регистрационные номера партии товара или укажите, что их нет.

 [Подробнее о маркировке «Честный ЗНАК» в Базе знаний](https://seller-edu.ozon.ru/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/obyazatelnaya-markirovka-tovarov)

 Получите статусы передачи маркировок:

- [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) — получить статус добавления экземпляров.
- [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) — получить данные созданных экземпляров.

4. До окончания времени на сборку подтвердите, что вы собрали
 заказ: [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4). Вы не сможете собрать заказ, если:
 - заказ не в статусе `awaiting_packaging`;
 - вы не указали коды маркировки для товаров, подлежащих обязательной маркировке.

 При необходимости используйте этот метод, чтобы разделить заказ на несколько отправлений. Например, если в заказе
 несколько товаров и их необходимо упаковать в разные коробки, так как вместе они не отвечают требованиям к упаковке.

 После использования метода статус отправления изменится на `awaiting_deliver`.

 Вы можете использовать метод для частичной
 сборки: [/v4/posting/fbs/ship/package](#operation/PostingAPI_ShipFbsPostingPackage).

5. После передачи отправления в службу доставки измените статус отправления на `delivering` —
 «Доставляется»: [/v2/fbs/posting/delivering](#operation/PostingAPI_FbsPostingDelivering).

6. Одновременно с этим, если у отправления есть трек-номер, передайте
 его: [/v2/fbs/posting/tracking-number/set](#operation/PostingAPI_FbsPostingTrackingNumberSet).

7. Когда курьер едет к покупателю, поменяйте статус отправления на «Последняя
 миля»: [/v2/fbs/posting/last-mile](#operation/PostingAPI_FbsPostingLastMile).

8. Когда курьер передал отправление покупателю, поменяйте статус на
 «Доставлено»: [/v2/fbs/posting/delivered](#operation/PostingAPI_FbsPostingDelivered).

## Схема rFBS Crossborder с интегрированной службой доставки

1. Перед началом работы с отправлениями получите список необработанных заказов (отправлений):
 [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Если покупатель юридическое лицо, то в блоке `requirements` будет информация о необходимости передать
 страну-производителя для всех товаров в заказе, у которых она не указана. 
 Получите список доступных для выбора
 стран: [/v2/posting/fbs/product/country/list](#operation/PostingAPI_ListCountryProductFbsPostingV2). Затем передайте
 информацию о
 стране-производителе: [/v2/posting/fbs/product/country/set](#operation/PostingAPI_SetCountryProductFbsPostingV2).

 Также можно получать список заказов (отправлений): [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3).
 Он позволяет получить все заказы, используя фильтры с различными статусами. Можно также получить данные аналитики,
 если поле `with` отправить со значением `analytics_data`.

 Отправления могут прийти в статусах `awaiting_packaging`, `awaiting_approve` или `awaiting_verification`.

2. Получите дополнительную информацию о заказах: [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3).

 В блоке `requirements` указывается:
 - какие товары подлежат обязательной маркировке;
 - нужно ли передать номер грузовой таможенной декларации и регистрационный номер партии товара — эту информацию
 также можно получить с помощью методов [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)
 и [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

 Дополнительную информацию вы также можете получить по
 штрихкоду: [/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode).

3. Проверьте, что коды маркировки соответствуют требованиям системы «Честный ЗНАК» по составу и количеству
 символов: [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5).

 С помощью метода [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) добавьте для каждого экземпляра маркировку, которую будете передавать в систему «Честный ЗНАК». При необходимости передайте
 номера таможенных деклараций и регистрационные номера партии товара или укажите, что их нет.

 [Подробнее о маркировке «Честный ЗНАК» в Базе знаний](https://seller-edu.ozon.ru/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/obyazatelnaya-markirovka-tovarov)

 Получите статусы передачи маркировок:

- [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) — получить статус добавления экземпляров.
- [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) — получить данные созданных экземпляров.

4. До окончания времени на сборку подтвердите, что вы собрали
 заказ: [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4). Вы не сможете собрать заказ, если:
 - заказ не в статусе `awaiting_packaging`;
 - вы не указали коды маркировки для товаров, подлежащих обязательной маркировке.

 При необходимости используйте этот метод, чтобы разделить заказ на несколько отправлений. Например, если в заказе
 несколько товаров и их необходимо упаковать в разные коробки, так как вместе они не отвечают требованиям к упаковке.

 После использования метода статус отправления изменится на `awaiting_deliver`.

 Вы можете использовать метод для частичной
 сборки: [/v4/posting/fbs/ship/package](#operation/PostingAPI_ShipFbsPostingPackage).

5. Для каждого отправления распечатайте этикетку для идентификации в системе
 Ozon: [/v2/posting/fbs/package-label](#operation/PostingAPI_PostingFBSPackageLabel).

Передайте отправление в службу доставки. Все статусы от «Доставляется» до «Доставлено» будет передавать служба доставки.

### Отменить доставку отправления

1. Используйте [/v2/posting/fbs/cancel-reason/list](#operation/PostingAPI_GetPostingFbsCancelReasonList) на любом этапе
 работы с отправлением, чтобы получить список причин отмены отправления.

2. Передайте этот список и номер отправления: [/v2/posting/fbs/cancel](#operation/PostingAPI_CancelFbsPosting).

Чтобы отменить часть товаров в отправлении,
используйте [/v2/posting/fbs/product/cancel](#operation/PostingAPI_CancelFbsPostingProduct).

Если отправление отменит покупатель, статус изменится на `cancelled`.

## Как работать с заказами с весовыми товарами (rFBS)

Перед тем, как перевести заказ с весовыми товарами в статус «Ожидает отгрузки» — `awaiting_delivery`, передайте
уточнённые данные о весе товаров. Для этого после взвешивания перед сборкой передайте информацию о весе
каждого экземпляра весовых товаров через метод [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).

Метод [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6)
вернёт ошибки:
- `WEIGHT_IS_OUT_OF_RANGE` — если вы передали вес, который выходит за границы допустимого;
- `WEIGHT_IS_REQUIRED` — если вы не передали вес для весовых товаров.

Если в методе [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3)
в параметре `result.products.is_weight_needed` для товара указано значение `true`, взвесьте товар.

После передачи корректного веса для всех экземпляров всех весовых товаров вы сможете перевести отправление в статус
«Ожидает отгрузки» — `awaiting_delivery`.

Если в заказе с весовыми товарами есть невзвешенные товары, при вызове метода [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4) 
вернётся ошибка `WEIGHT_IS_REQUIRED`.

## Схема FBP

### Прямая поставка

1. [/v1/fbp/warehouse/list](#operation/FbpWarehouseList) — получите список партнёрских складов.
2. [/v1/fbp/draft/direct/product/validate](#operation/FbpDraftDirectProductValidate) — передайте список товаров, чтобы проверить, может ли склад партнёра их принять.
3. [/v1/fbp/draft/direct/timeslot/get](#operation/FbpDraftDirectGetTimeslot) — получите список таймслотов для прямой поставки.
4. Выберите способ доставки:
 
 Доставка силами продавца

 • [/v1/fbp/draft/direct/seller-dlv/create](#operation/FbpDraftDirectSellerDlvCreate) — создайте черновик заявки на поставку.
 
 • [/v1/fbp/draft/direct/timeslot/edit](#operation/FbpDraftDirectTimeslotEdit) — измените таймслот для поставки в черновике заявки.
 
 • [/v1/fbp/draft/direct/seller-dlv/edit](#operation/FbpDraftDirectSellerDlvEdit) — обновите информацию о доставке силами продавца в черновике заявки. 

 
 
 Доставка силами сторонней транспортной компании

 • [/v1/fbp/draft/direct/tpl-dlv/create](#operation/FbpAPI_FbpDraftDirectTplDlvCreate) — создайте черновик заявки на поставку.
 
 • [/v1/fbp/draft/direct/timeslot/edit](#operation/FbpDraftDirectTimeslotEdit) — измените таймслот для поставки в черновике заявки.
 
 • [/v1/fbp/draft/direct/tpl-dlv/edit](#operation/FbpAPI_FbpDraftDirectTplDlvEdit) — обновите информацию о доставке силами сторонней траспортной компании в черновике заявки.

 

details {
 margin-bottom: 10px;
 border: 1px solid #ddd;
 padding: 10px;
 border-radius: 5px;
}
summary {
 cursor: pointer;
 font-weight: bold;
}

5. [/v1/fbp/draft/list](#operation/FbpAPI_FbpDraftList) — получите список черновиков.
6. [/v1/fbp/draft/get](#operation/FbpAPI_FbpDraftGet) — получите информацию о черновике на поставку. Если в черновике есть ошибка, используйте [/v1/fbp/draft/direct/delete](#operation/FbpDraftDirectDelete), чтобы удалить его.
7. [/v1/supply-order/bundle](#operation/SupplyOrderBundle) — получите информацию по товарному составу с помощью `bundle_id`.
8. [/v1/fbp/draft/direct/registrate](#operation/FbpDraftDirectRegistrate) — переведите черновик заявки на поставку в активную заявку.
9. [/v1/fbp/order/direct/timeslot/list](#operation/FbpAPI_FbpAvailableTimeslotList) — получите актуальные таймслоты склада для поставки.
10. [/v1/fbp/order/direct/timeslot/edit](#operation/FbpAPI_FbpEditTimeslot) — измените актуальный таймслот поставки.
11. [/v1/fbp/order/direct/seller-dlv/edit](#operation/FbpAPI_FbpOrderDirectSellerDlvEdit) или [/v1/fbp/order/direct/tpl-dlv/edit](#operation/FbpOrderDirectTplDlvEdit) — передайте актуальную информацию о доставке, если доставляете самостоятельно или через транспортную компанию.
12. [/v1/fbp/order/list](#operation/FbpAPI_FbpOrderList) — получите список поставок.
13. [/v1/fbp/order/get](#operation/FbpAPI_FbpOrderGet) — получите информацию о конкретной поставке. Если в заявке на поставку есть ошибка, используйте [/v1/fbp/order/direct/cancel](#operation/FbpAPI_FbpOrderDirectCancel), чтобы отменить поставку.
14. [/v1/fbp/label/create](#operation/FbpAPI_FbpCreateLabel) — создайте задание на генерацию этикеток.
15. [/v1/fbp/label/get](#operation/FbpAPI_FbpGetLabel) — получите этикетки и статус задания на их генерацию.
16. [/v1/fbp/act-to/create](#operation/FbpAPI_FbpCreateConsignmentNote) — создайте задание на генерацию транспортной накладной.
17. [/v1/fbp/act-to/get](#operation/FbpAPI_FbpCheckConsignmentNoteState) — получите транспортную накладную и статус задания на её генерацию.
18. [/v1/fbp/act-from/create](#operation/FbpAPI_FbpCreateAct) — создайте задание на генерацию акта приёмки.
19. [/v1/fbp/act-from/get](#operation/FbpAPI_FbpCheckActState) — получите акт приёмки и статус задания на его генерацию.
20. [/v1/fbp/archive/list](#operation/FbpAPI_FbpArchiveList) — получите список завершённых поставок.
21. [/v1/fbp/archive/get](#operation/FbpAPI_FbpArchiveGet) — получите информацию о конкретной завершённой поставке.

### Поставка на партнёрский пункт приёма заказов

1. [/v1/fbp/warehouse/list](#operation/FbpWarehouseList) — получите список партнёрских складов.
2. [/v1/fbp/draft/drop-off/product/validate](#operation/FbpDraftDropOffProductValidate) — проверьте, может ли склад партнёра принять товары.
3. [/v1/fbp/draft/drop-off/province/list](#operation/FbpDraftDropOffProvinceList) — получите список провинций.
4. [/v1/fbp/draft/drop-off/point/list](#operation/FbpDraftDropOffPointList) — получите список пунктов в провинции.
5. [/v1/fbp/draft/drop-off/point/timetable](#operation/FbpDraftDropOffPointTimetable) — получите расписание пункта.
6. [/v1/fbp/draft/drop-off/create](#operation/FbpDraftDropOffCreate) — создайте черновик для drop-off доставки.
7. [/v1/fbp/draft/drop-off/dlv/edit](#operation/FbpDraftDropOffDlvEdit) — измените детали drop-off доставки для черновика.
8. [/v1/fbp/draft/list](#operation/FbpAPI_FbpDraftList) — получите список черновиков.
9. [/v1/fbp/draft/get](#operation/FbpAPI_FbpDraftGet) — получите информацию о конкретном черновике поставки. Если в черновике есть ошибка, используйте [/v1/fbp/draft/drop-off/delete](#operation/FbpDraftDropOffDelete), чтобы удалить его.
10. [/v1/supply-order/bundle](#operation/SupplyOrderBundle) — получите информацию по товарному составу с помощью `bundle_id`.
11. [/v1/fbp/draft/drop-off/registrate](#operation/FbpDraftDropOffRegistrate) — переведите черновик заявки на поставку в активную заявку.
12. [/v1/fbp/order/drop-off/timetable](#operation/FbpAPI_FbpOrderDropOffTimetable) — получите график работы drop-off пункта.
13. [/v1/fbp/order/drop-off/dlv/edit](#operation/FbpAPI_FbpOrderDropOffDlvEdit) — отредактируйте и передайте информацию о доставке на drop-off пункт.
14. [/v1/fbp/order/list](#operation/FbpAPI_FbpOrderList) — получите список поставок.
15. [/v1/fbp/order/get](#operation/FbpAPI_FbpOrderGet) — получите информацию о конкретной поставке. Если в заявке на поставку есть ошибка, используйте [/v1/fbp/order/drop-off/cancel](#operation/FbpAPI_FbpOrderDropOffCancel), чтобы отменить поставку.
16. [/v1/fbp/label/create](#operation/FbpAPI_FbpCreateLabel) — создайте задание на генерацию этикеток.
17. [/v1/fbp/label/get](#operation/FbpAPI_FbpGetLabel) — получите этикетки и статус задания на их генерацию.
18. [/v1/fbp/act-to/create](#operation/FbpAPI_FbpCreateConsignmentNote) — создайте задание на генерацию транспортной накладной.
19. [/v1/fbp/act-to/get](#operation/FbpAPI_FbpCheckConsignmentNoteState) — получите транспортную накладную и статус задания на её генерацию.
20. [/v1/fbp/act-from/create](#operation/FbpAPI_FbpCreateAct) — создайте задание на генерацию акта приёмки.
21. [/v1/fbp/act-from/get](#operation/FbpAPI_FbpCheckActState) — получите акт приёмки и статус задания на его генерацию.
22. [/v1/fbp/archive/list](#operation/FbpAPI_FbpArchiveList) — получите список завершённых поставок.
23. [/v1/fbp/archive/get](#operation/FbpAPI_FbpArchiveGet) — получите информацию о конкретной завершённой поставке.

### Вывоз товаров со склада продавца

1. [/v1/fbp/warehouse/list](#operation/FbpWarehouseList) — получите список партнёрских складов.
2. [/v1/fbp/draft/pick-up/product/validate](#operation/FbpAPI_FbpDraftPickUpProductValidate) — проверьте, может ли склад партнёра принять товары.
3. [/v1/fbp/draft/pick-up/create](#operation/FbpAPI_FbpOrderPickUpDlvEdit) — создайте черновик для pick-up доставки.
4. [/v1/fbp/draft/pick-up/dlv/edit](#operation/FbpAPI_FbpOrderPickUpDlvEdit) — измените детали pick-up доставки для черновика.
5. [/v1/fbp/draft/list](#operation/FbpAPI_FbpDraftList) — получите список черновиков.
6. [/v1/fbp/draft/get](#operation/FbpAPI_FbpDraftGet) — получите информацию о конкретном черновике поставки. Если в черновике есть ошибка, используйте [/v1/fbp/draft/pick-up/delete](#operation/FbpAPI_FbpDraftPickUpDelete), чтобы удалить его.
7. [/v1/supply-order/bundle](#operation/SupplyOrderBundle) — получите информацию по товарному составу с помощью `bundle_id`.
8. [/v1/fbp/draft/pick-up/registrate](#operation/FbpDraftPickUpRegistrate) — переведите черновик заявки на поставку в активную заявку.
9. [/v1/fbp/order/pick-up/dlv/edit](#operation/FbpAPI_FbpOrderPickUpDlvEdit) — измените информацию о pick-up пункте.
10. [/v1/fbp/order/list](#operation/FbpAPI_FbpOrderList) — получите список поставок.
11. [/v1/fbp/order/get](#operation/FbpAPI_FbpOrderGet) — получите информацию о конкретной поставке. Если в заявке на поставку есть ошибка, используйте [/v1/fbp/order/pick-up/cancel](#operation/FbpAPI_FbpOrderPickUpCancel), чтобы отменить поставку.
12. [/v1/fbp/label/create](#operation/FbpAPI_FbpCreateLabel) — создайте задание на генерацию этикеток.
13. [/v1/fbp/label/get](#operation/FbpAPI_FbpGetLabel) — получите этикетки и статус задания на их генерацию.
14. [/v1/fbp/act-to/create](#operation/FbpAPI_FbpCreateConsignmentNote) — создайте задание на генерацию транспортной накладной.
15. [/v1/fbp/act-to/get](#operation/FbpAPI_FbpCheckConsignmentNoteState) — получите транспортную накладную и статус задания на её генерацию.
16. [/v1/fbp/act-from/create](#operation/FbpAPI_FbpCreateAct) — создайте задание на генерацию акта приёмки.
17. [/v1/fbp/act-from/get](#operation/FbpAPI_FbpCheckActState) — получите акт приёмки и статус задания на его генерацию.
18. [/v1/fbp/archive/list](#operation/FbpAPI_FbpArchiveList) — получите список завершённых поставок.
19. [/v1/fbp/archive/get](#operation/FbpAPI_FbpArchiveGet) — получите информацию о конкретной завершённой поставке.

# Работа с архивом актов

- [/v2/posting/fbs/act/list](#operation/PostingAPI_FbsActList) — получите список сформированных ранее актов.
- [/v2/posting/fbs/act/get-postings](#operation/PostingAPI_ActPostingList) — получите список отправлений по каждому
 акту.

# Получите информацию о возвратах товаров

[/v1/returns/list](#operation/returnsList) — получите информацию о возвращённых товарах.

# Получите возвратные отгрузки по штрихкоду

Убедитесь, что вы можете получать возвратные отгрузки по штрихкоду: [/v1/return/giveout/is-enabled](#operation/ReturnAPI_GiveoutIsEnabled). Если у вас есть доступ, в параметре `enabled` будет указано значение `true`.

Чтобы получить возвратную отгрузку, запросите штрихкод:
- [/v1/return/giveout/get-pdf](#operation/ReturnAPI_GiveoutGetPDF) — получить штрихкод в формате PDF.
- [/v1/return/giveout/get-png](#operation/ReturnAPI_GiveoutGetPNG) — получить штрихкод в формате PNG.
- [/v1/return/giveout/barcode](#operation/ReturnAPI_GiveoutGetBarcode) — получить штрихкод в текстовом виде.

Получите информацию и список возвратных отгрузок:
- [/v1/return/giveout/list](#operation/ReturnAPI_GiveoutList) — получить список возвратных отгрузок.
- [/v1/return/giveout/info](#operation/ReturnAPI_GiveoutInfo) — получить информацию о выбранной отгрузке.
 
Вы можете забрать возвраты отдельно от поставки товаров. Если для проезда на склад Ozon нужен пропуск, создайте его с помощью метода [/v1/return/pass/create](#operation/returnPassCreate).
Для каждого проезда за возвратами нужен новый пропуск.

Для редактирования и удаления пропуска используйте методы [/v1/return/pass/update](#operation/returnPassUpdate) и [/v1/return/pass/delete](#operation/returnPassDelete).
 
Список всех пропусков можно получить с помощью метода [/v1/pass/list](#operation/PassList).

[Подробнее об оформлении пропусков](https://seller-edu.ozon.ru/fbs/ozon-logistika/oformlenie-propuska)

# Управляйте заявками на возврат rFBS-заказов

Получите заявки и информацию о них:

- [/v2/returns/rfbs/get](#operation/RFBSReturnsAPI_ReturnsRfbsGetV2) — получите информацию по
 заявке на возврат rFBS.
- [/v2/returns/rfbs/list](#operation/RFBSReturnsAPI_ReturnsRfbsListV2) — получите список
 заявок на возврат rFBS.

Вы можете одобрить, компенсировать, подтвердить возврат денег, запросить товар для проверки и отклонить заявку методом [/v1/returns/rfbs/action/set](#operation/ReturnsAPI_ReturnsRfbsActionSet). 
Для передачи корректного `action` получите список доступных для конкретного возврата, в методе [/v2/returns/rfbs/get](#operation/RFBSReturnsAPI_ReturnsRfbsGetV2).

# Управляйте заявками на отмену

Получите заявки и информацию о них: [/v2/conditional-cancellation/list](#operation/CancellationAPI_GetConditionalCancellationListV2).

Примите решение по новой заявке на отмену — подтвердите или отклоните её:

- [/v2/conditional-cancellation/approve](#operation/CancellationAPI_ConditionalCancellationApproveV2) — подтвердите заявку
 на отмену rFBS. Заказ будет автоматически отменён, а деньги вернутся покупателю.
- [/v2/conditional-cancellation/reject](#operation/CancellationAPI_ConditionalCancellationRejectV2) — отклоните заявку на
 отмену rFBS. Заказ останется в том же статусе, и его нужно будет доставить покупателю.

# Управляйте чатами

Для получения списка чатов используйте [/v3/chat/list](#operation/ChatAPI_ChatListV3). В ответе будут идентификаторы текущих чатов и последних сообщений.

Для отправки сообщений по идентификатору чата используйте методы:

- [/v1/chat/send/message](#operation/ChatAPI_ChatSendMessage) — для отправки текстового сообщения.

- [/v1/chat/send/file](#operation/ChatAPI_ChatSendFile) — для отправки файла или изображения.

Для получения истории чата по идентификатору чата или сообщения используйте метод [/v3/chat/history](#operation/ChatAPI_ChatHistoryV3). Направление сортировки по
 умолчанию — от новых сообщений к старым.

Если указать идентификатор сообщения, то история начнётся с этого сообщения.

Чтобы создать новый чат с покупателем по номеру отправления,
воспользуйтесь [/v1/chat/start](#operation/ChatAPI_ChatStart).

Чтобы отметить сообщение и все сообщения до него прочитанными,
используйте [/v2/chat/read](#operation/ChatAPI_ChatReadV2).

# Создайте и получите отчёты

При запросе любого из отчётов сначала возвращается код на создание документа. Отправьте его в запросе метода
[/v1/report/info](#operation/ReportAPI_ReportInfo) — в ответе вернётся файл отчёта и дополнительная информация.

Чтобы получить список сформированных ранее отчётов, используйте [/v1/report/list](#operation/ReportAPI_ReportList).

Методы для получения отчётов:

- [/v1/report/products/create](#operation/ReportAPI_CreateCompanyProductsReport) — отчёт с данными о товарах, например
 Ozon&nbsp;ID, описанием товара, цены, комиссии или габаритов упаковки.

- [/v3/finance/transaction/list](#operation/FinanceAPI_FinanceTransactionListV3) — отчёт по транзакциям,
 доступный в личном кабинете продавца.

- [/v4/product/info/price](#operation/ProductAPI_GetProductInfoPricesV4) — отчёт по ценам.

- [/v1/report/warehouse/stock](#operation/ReportAPI_CreateStockByWarehouseReport) — отчёт по остаткам на складе.

- [/v2/report/returns/create](#operation/ReportAPI_ReportReturnsCreate) — отчёт о возвращённых товарах для FBS и
 rFBS. Отчёт содержит товары, принятые от покупателя, готовые к получению или переданные продавцу.

- [/v1/report/postings/create](#operation/ReportAPI_CreateCompanyPostingsReport) — отчёт об отправлениях.

- [/v1/finance/cash-flow-statement/list](#operation/FinanceAPI_FinanceCashFlowStatementList) — финансовый отчёт.

- [/v1/report/discounted/create](#operation/ReportAPI_CreateDiscountedReport) — отчёт об уценённых товарах.

# Получите аналитические отчёты

- [/v1/analytics/data](#operation/AnalyticsAPI_AnalyticsGetData) — получите данные аналитики.

 Если укажете период и метрики, которые нужно рассчитать, в ответе будет аналитиĸа, сгруппированная по параметру
 `dimensions`.

- [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) — получите аналитику по остаткам товаров на складах.

Чтобы получить отчёт по оборачиваемости FBO, запросите его в [личном кабинете](https://seller.ozon.ru/app/analytics/fulfillment-reports/turnover).

# Получите финансовые отчёты

- [/v3/finance/transaction/list](#operation/FinanceAPI_FinanceTransactionListV3) — получите подробную информацию по
 транзакциям для отправления.

- [/v3/finance/transaction/totals](#operation/FinanceAPI_FinanceTransactionTotalV3) — получите детальную информацию по
 итоговым суммам транзакций за указанный период.

# Получите информацию о рейтинге

- [/v1/rating/summary](#operation/RatingAPI_RatingSummaryV1) — получите текущие значения рейтингов продавца.

- [/v1/rating/history](#operation/RatingAPI_RatingHistoryV1) — получите информацию о рейтингах продавца за период и
 количество штрафных баллов, начисленных в Premium-программе.
