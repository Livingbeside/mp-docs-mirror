---
title: Информация о заказах в кабинете
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/orders
operation_id: getBusinessOrders
tags:
  - orders
  - fbs
  - dbs
  - fby
  - express
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 0c474a2982be4830
---

# Информация о заказах в кабинете

`POST /v1/businesses/{businessId}/orders`

{% include notitle [access](../../_auto/method_scopes/getBusinessOrders.md) %}

Возвращает информацию о заказах в кабинете. Запрос можно использовать для отслеживания заказов и их статусов.

{% note tip "Вы также можете настроить API-уведомления" %}

Маркет отправит вам [запрос](../../push-notifications/reference/sendNotification.md), когда появится новый заказ или изменится его статус. А полную информацию можно получить с помощью этого метода.

[{#T}](../../push-notifications/index.md)

{% endnote %}

Доступна фильтрация по параметрам:

* дата оформления заказа;

* дата и время обновления заказа;

* дата отгрузки;

* статусы заказов (`statuses`);

* этапы обработки или причины отмены (`substatuses`);

* идентификаторы кампаний;

* идентификаторы заказов;

* внешние идентификаторы заказов;

* тип заказа (настоящий или тестовый);

* модели размещения;

* наличие запросов от покупателей на отмену заказа.

Максимальный диапазон дат за один запрос — 30 дней (передается в параметрах `fromDate` и `toDate`). Если их не передать, возвращается информация за последние 30 дней.

Результаты возвращаются постранично. Для навигации используйте параметры `pageToken` и `limit`.

Получить более подробную информацию о покупателе и его номере телефона можно с помощью запроса [GET v2/campaigns/{campaignId}/orders/{orderId}/buyer](../../reference/order-delivery/getOrderBuyerInfo.md).

{% include notitle [limit](../../_auto/method_limits/getBusinessOrders.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | — |

## Запрос

**Тело запроса** (`application/json`):

- `orderIds` — array[integer<int64>]. Идентификаторы заказов.
- `externalOrderIds` — array[string]. Внешние идентификаторы заказов.
- `programTypes` — array[string (FBY, FBS, DBS, EXPRESS, LAAS)]. Модели работы магазина на Маркете.
- `campaignIds` — array[integer<int64>]. Идентификаторы кампаний магазинов.
- `statuses` — array[string (PLACING, RESERVED, UNPAID, PROCESSING, DELIVERY, PICKUP, DELIVERED, CANCELLED, PENDING, PARTIALLY_RETURNED, RETURNED, UNKNOWN)]. Статусы заказов.
- `substatuses` — array[string (RESERVATION_EXPIRED, USER_NOT_PAID, USER_UNREACHABLE, USER_CHANGED_MIND, USER_REFUSED_DELIVERY, USER_REFUSED_PRODUCT, SHOP_FAILED, USER_REFUSED_QUALITY, REPLACING_ORDER, PROCESSING_EXPIRED, PENDING_EXPIRED, SHOP_PENDING_CANCELLED…)]. Этапы обработки или причины отмены заказов.
- `dates` — object. Даты заказов.
  - `creationDateFrom` — string<date>. Начальная дата для фильтрации заказов по дате оформления. Формат даты: `ГГГГ-ММ-ДД`. Между начальной и конечной датой (параметр `creationDateTo`) должно быть не больше 30 дней. Значение по умолчанию: 30 дней назад от текущей даты. Начальная дата включается в интервал для фильтрации.
  - `creationDateTo` — string<date>. Конечная дата для фильтрации заказов по дате оформления. Формат даты: `ГГГГ-ММ-ДД`. Между начальной (параметр `creationDateFrom`) и конечной датой должно быть не больше 30 дней. Значение по умолчанию: текущая дата. Если промежуток времени между `creationDateTo` и `creationDateFrom` меньше суток, то `creationDateTo` равен `creationDateFrom` + сутки. Конечная дата не включается в интервал для фильтрации.
  - `shipmentDateFrom` — string<date>. Начальная дата для фильтрации заказов по дате отгрузки в службу доставки (параметр `shipmentDate`). Формат даты: `ГГГГ-ММ-ДД`. Между начальной и конечной датой (параметр `shipmentDateTo`) должно быть не больше 30 дней. Начальная дата включается в интервал для фильтрации.
  - `shipmentDateTo` — string<date>. Конечная дата для фильтрации заказов по дате отгрузки в службу доставки (параметр `shipmentDate`). Формат даты: `ГГГГ-ММ-ДД`. Между начальной (параметр `shipmentDateFrom`) и конечной датой должно быть не больше 30 дней. Если промежуток времени между `shipmentDateTo` и `shipmentDateFrom` меньше суток, то `shipmentDateTo` равен `shipmentDateFrom` + сутки. Конечная дата не включается в интервал для фильтрации.
  - `updateDateFrom` — string<date-time>. Начальная дата обновления заказа (ISO 8601).
  - `updateDateTo` — string<date-time>. Конечная дата обновления заказа (ISO 8601).
- `fake` — boolean. Тип заказа: * `false` — настоящий заказ покупателя. * `true` — [тестовый заказ](../../concepts/sandbox.md) Маркета.
- `waitingForCancellationApprove` — boolean. **Только для модели DBS** Фильтр для получения заказов, по которым есть запросы на отмену. При значении `true` возвращаются только те заказы, которые находятся в статусе `DELIVERY` или `PICKUP`, и пользователи решили их отменить.
- `sourcePlatforms` — array[string (MARKET, OZON, WILDBERRIES, OTHER)]. Площадки-источники заказов.

## Ответы

**200** — Список заказов в кабинете.

- `orders` — array[object] **обязательный**. Список заказов в кабинете.
  - `orderId` — integer<int64> **обязательный**. Идентификатор заказа.
  - `campaignId` — integer<int64> **обязательный**. Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия. Его можно узнать с помощью запроса [GET v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**: * блок **Идентификатор кампании**; * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**. ⚠️ Не путайте его с: - идентификатором магазина, который отображается в личном кабинете продавца; - рекламными кампаниями.
  - `programType` — string (FBY, FBS, DBS, EXPRESS, LAAS). Тип программы кампании магазина.
  - `externalOrderId` — string. Внешний идентификатор заказа, который вы передали в [POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](../../reference/orders/updateExternalOrderId.md).
  - `status` — string (PLACING, RESERVED, UNPAID, PROCESSING, DELIVERY, PICKUP, DELIVERED, CANCELLED, PENDING, PARTIALLY_RETURNED, RETURNED, UNKNOWN) **обязательный**. Статус заказа: * `PLACING` — оформляется, подготовка к резервированию. * `RESERVED` — зарезервирован, но недооформлен (только для LaaS). * `UNPAID` — оформлен, но еще не оплачен (если выбрана оплата при оформлении). * `PROCESSING` — находится в обработке. * `DELIVERY` — передан в службу доставки. * `PICKUP` — доставлен в пункт выдачи. * `DELIVERED` — получен покупателем. * `CANCELLED` — отменен. * `PENDING` — ожидает обработки со стороны продавца. * `PARTIALLY_RETURNED` — возвращен частично. * `RETURNED` — возвращен полностью. * `UNKNOWN` — неизвестный статус. Также могут возвращаться другие значения. Обрабатывать их не нужно.
  - `substatus` — string (RESERVATION_EXPIRED, USER_NOT_PAID, USER_UNREACHABLE, USER_CHANGED_MIND, USER_REFUSED_DELIVERY, USER_REFUSED_PRODUCT, SHOP_FAILED, USER_REFUSED_QUALITY, REPLACING_ORDER, PROCESSING_EXPIRED, PENDING_EXPIRED, SHOP_PENDING_CANCELLED…) **обязательный**. Этап обработки заказа (статус `PROCESSING`) или причина отмены заказа (статус `CANCELLED`). * Значения для заказа в статусе `PROCESSING`: * `STARTED` — заказ подтвержден, его можно начать обрабатывать. * `READY_TO_SHIP` — заказ собран и готов к отправке. * Значения для заказа в статусе `CANCELLED`: * `RESERVATION_EXPIRED` — покупатель не завершил оформление зарезервированного заказа в течение 10 минут. * `USER_NOT_PAID` — покупатель не оплатил заказ (для типа оплаты `PREPAID`) в течение 30 минут. * `USER_UNREACHABLE` — не удалось связаться с покупателем. Для отмены с этой причиной необходимо выполнить условия: * не менее 3 звонков с 8 до 21 в часовом поясе покупателя; * перерыв между первым и третьим звонком не менее 90 минут; * соединение не короче 5 секунд. Если хотя бы одно из этих условий не выполнено (кроме случая, когда номер недоступен), отменить заказ не получится. Вернется ответ с кодом ошибки 400. * `USER_CHANGED_MIND` — покупатель отменил заказ по личным причинам. * `USER_REFUSED_DELIVERY` — покупателя не устроили условия доставки. * `USER_REFUSED_PRODUCT` — покупателю не подошел товар. * `SHOP_FAILED` — магазин не может выполнить заказ. * `USER_REFUSED_QUALITY` — покупателя не устроило качество товара. * `USER_IDENTIFICATION_MISMATCH` — идентификационный документ покупателя не совпадает с данными в заказе. * `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED` — заказ участвовал в групповой покупке и был отменен, потому что не было достигнуто нужное количество покупок. * `REPLACING_ORDER` — покупатель решил заменить товар другим по собственной инициативе. * `PROCESSING_EXPIRED` — значение более не используется. * `PICKUP_EXPIRED` — закончился срок хранения заказа в пункт выдачи. * `TOO_MANY_DELIVERY_DATE_CHANGES` — заказ переносили слишком много раз. * `TOO_LONG_DELIVERY` — заказ доставляется слишком долго. * `INCORRECT_PERSONAL_DATA` — для заказа из-за рубежа указаны неправильные данные получателя, заказ не пройдет проверку на таможне. * `TECHNICAL_ERROR` — техническая ошибка на стороне Маркета. Обратитесь в поддержку. Также могут возвращаться другие значения. Обрабатывать их не нужно.
  - `creationDate` — string<date-time> **обязательный**. Дата и время оформления заказа. Формат даты: ISO 8601 со смещением относительно UTC.
  - `updateDate` — string<date-time>. Дата и время последнего обновления заказа. Формат даты: ISO 8601 со смещением относительно UTC.
  - `paymentType` — string (PREPAID, POSTPAID, UNKNOWN) **обязательный**. Тип оплаты заказа: * `PREPAID` — оплата при оформлении заказа. * `POSTPAID` — оплата при получении заказа. * `UNKNOWN` — неизвестный тип. Если параметр отсутствует, заказ будет оплачен при получении.
  - `paymentMethod` — string (CASH_ON_DELIVERY, CARD_ON_DELIVERY, BOUND_CARD_ON_DELIVERY, BNPL_BANK_ON_DELIVERY, BNPL_ON_DELIVERY, YANDEX, APPLE_PAY, EXTERNAL_CERTIFICATE, CREDIT, GOOGLE_PAY, TINKOFF_CREDIT, SBP…) **обязательный**. Способ оплаты заказа: * Значения, если выбрана оплата при оформлении заказа (`"paymentType": "PREPAID"`): * `YANDEX` — банковской картой. * `APPLE_PAY` — Apple Pay (не используется). * `GOOGLE_PAY` — Google Pay (не используется). * `CREDIT` — в кредит. * `TINKOFF_CREDIT` — в кредит в Тинькофф Банке. * `TINKOFF_INSTALLMENTS` — рассрочка в Тинькофф Банке. * `EXTERNAL_CERTIFICATE` — подарочным сертификатом (например, из приложения «Сбербанк Онлайн»). * `SBP` — через систему быстрых платежей. * `B2B_ACCOUNT_PREPAYMENT` — заказ оплачивает организация. * `MICROCREDIT` - Сплит на основе МКК (Микрокредитной компании). * `BNPL_TBC` - BNPL через внешний банк TBC. * `DIGITAL_RUBLE` - Цифровой рубль. * Значения, если выбрана оплата при получении заказа (`"paymentType": "POSTPAID"`): * `CARD_ON_DELIVERY` — банковской картой. * `BOUND_CARD_ON_DELIVERY` — привязанной картой при получении. * `BNPL_BANK_ON_DELIVERY` — супер Сплитом. * `BNPL_ON_DELIVERY` — Сплитом. * `BNPL_TBYB` - Оплата после доставки на основе Сплита. * `CASH_ON_DELIVERY` — наличными. * `B2B_ACCOUNT_POSTPAYMENT` — заказ оплачивает организация после доставки. * `UNKNOWN` — неизвестный тип. Значение по умолчанию: `CASH_ON_DELIVERY`.
  - `fake` — boolean **обязательный**. Тип заказа: * `false` — настоящий заказ покупателя. * `true` — [тестовый заказ](../../concepts/sandbox.md) Маркета.
  - `items` — array[object] **обязательный**. Список товаров в заказе.
    - `id` — integer<int64> **обязательный**. Идентификатор товара в заказе. Позволяет идентифицировать товар в рамках заказа.
    - `offerId` — string **обязательный**. Идентификатор товарного предложения.
    - `offerName` — string **обязательный**. Название товара.
    - `count` — integer **обязательный**. Количество единиц товара.
    - `prices` — object. Информация о выплатах и вознаграждениях.
      - `payment` — object. Общая стоимость всех единиц товара.
        - `value` — number **обязательный**. Значение.
        - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
      - `subsidy` — object. Общая сумма вознаграждений продавцу.
        - `value` — number **обязательный**. Значение.
        - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
      - `cashback` — object. Сумма, которая оплачена баллами Плюса.
        - `value` — number **обязательный**. Значение.
        - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
      - `vat` — string (NO_VAT, VAT_0, VAT_10, VAT_10_110, VAT_20, VAT_20_120, VAT_18, VAT_18_118, VAT_12, VAT_05, VAT_07, VAT_22…). НДС на товар.
    - `instances` — array[object]. Информация о маркировке единиц товара. Возвращаются данные для маркировки, переданные в запросе: * Для DBS — [PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](../../reference/orders/provideOrderItemIdentifiers.md) или [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](../../reference/orders/setOrderBoxLayout.md). * Для FBS и EXPRESS — [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](../../reference/orders/setOrderBoxLayout.md). Для FBY возвращаются коды маркировки, переданные во время поставки. Если магазин еще не передавал коды для этого заказа, `instances` отсутствует.
      - `cis` — string. Код идентификации единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) без криптохвоста или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
      - `cisFull` — string. Код идентификации единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) с криптохвостом.
      - `uin` — string. УИН ювелирного изделия (16-значный код) Производитель получает УИН, когда регистрирует изделие в системе контроля за оборотом драгоценных металлов и камней — ГИИС ДМДК.
      - `rnpt` — string. Регистрационный номер партии товара. Представляет собой строку из четырех чисел, разделенных косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ/ХХХ. Первая часть — код таможни, которая зарегистрировала декларацию на партию товара. Далее — дата, номер декларации и номер маркированного товара в декларации.
      - `gtd` — string. Грузовая таможенная декларация. Представляет собой строку из трех чисел, разделенных косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ. Первая часть — код таможни, которая зарегистрировала декларацию на ввезенные товары. Далее — дата и номер декларации.
      - `countryCode` — string. Страна производства в формате ISO 3166-1 alpha-2. [Как получить](../../reference/regions/getRegionsCodes.md)
    - `requiredInstanceTypes` — array[string (CIS, CIS_OPTIONAL, UIN, RNPT, GTD)]. Список необходимых маркировок товара.
    - `itemStatuses` — array[object]. Информация о статусах отдельных единиц товара в заказе. Если данных о статусах отдельных единиц товара нет, поле отсутствует.
      - `status` — string (CREATED, SHIPPED, CANCELLED, DELIVERED_TO_BUYER, LOST, REJECTED, RETURNED) **обязательный**. Статус единицы товара в заказе. * `CREATED` — создана. * `SHIPPED` — передана в доставку. * `CANCELLED` — отменена или удалена из заказа. * `DELIVERED_TO_BUYER` — передана покупателю. * `LOST` — утеряна. * `REJECTED` — невыкупленная. * `RETURNED` — возвращенная.
      - `count` — integer<int64> **обязательный**. Количество единиц товара.
    - `tags` — array[string (ULTIMA, SAFE_TAG)]. Признаки товара.
  - `prices` — object. Информация о стоимости заказа, доставки и вознаграждениях.
    - `payment` — object. Сумма платежа покупателя.
      - `value` — number **обязательный**. Значение.
      - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
    - `subsidy` — object. Общая сумма вознаграждений продавцу.
      - `value` — number **обязательный**. Значение.
      - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
    - `cashback` — object. Сумма, которая оплачена баллами Плюса. Возвращается баллами.
      - `value` — number **обязательный**. Значение.
      - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
    - `delivery` — object. Информация о стоимости доставки, включая подъем на этаж.
      - `payment` — object. Платеж покупателя за доставку.
        - `value` — number **обязательный**. Значение.
        - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
      - `subsidy` — object. Вознаграждение Маркета за доставку.
        - `value` — number **обязательный**. Значение.
        - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
      - `vat` — string (NO_VAT, VAT_0, VAT_10, VAT_10_110, VAT_20, VAT_20_120, VAT_18, VAT_18_118, VAT_12, VAT_05, VAT_07, VAT_22…). НДС на доставку.
  - `delivery` — object **обязательный**. Информация о доставке заказа.
    - `type` — string (DELIVERY, PICKUP, POST, DIGITAL, UNKNOWN) **обязательный**. Способ доставки заказа.
    - `serviceName` — string **обязательный**. Название службы доставки.
    - `deliveryServiceId` — integer<int64> **обязательный**. Идентификатор службы доставки.
    - `warehouseId` — string. Идентификатор склада в системе магазина, на который сформирован заказ.
    - `deliveryPartnerType` — string (SHOP, YANDEX_MARKET, UNKNOWN) **обязательный**. Тип сотрудничества со службой доставки в рамках указанного заказа.
    - `dispatchType` — string (UNKNOWN, BUYER, MARKET_BRANDED_OUTLET, SHOP_OUTLET). Способ доставки: * `BUYER` — курьерская доставка покупателю. * `MARKET_BRANDED_OUTLET` — доставка в пункт выдачи заказов Маркета. * `SHOP_OUTLET` — доставка в пункт выдачи заказов магазина. * `UNKNOWN` — неизвестный тип.
    - `dates` — object **обязательный**. Диапазон дат доставки.
      - `fromDate` — string<date> **обязательный**. Ближайшая дата доставки. Формат даты: `ГГГГ-ММ-ДД`.
      - `toDate` — string<date>. Самая поздняя дата доставки. Если `toDate` не указан, считается дата в параметре `fromDate`. Формат даты: `ГГГГ-ММ-ДД`.
      - `fromTime` — string<time>. Начало интервала времени доставки. Передается только вместе с параметром `type=DELIVERY`. Формат времени: 24-часовой, `ЧЧ:ММ`. Вместо `ММ` всегда указывайте `00` (исключение — `23:59`). Минимальное значение: `00:00`.
      - `toTime` — string<time>. Конец интервала времени доставки. Передается только вместе с параметром `type=DELIVERY`. Формат времени: 24-часовой, `ЧЧ:ММ`. Вместо `ММ` всегда указывайте `00` (исключение — `23:59`). Максимальное значение: `23:59`.
      - `realDeliveryDate` — string<date>. Дата, когда товар доставлен до пункта выдачи заказа (в случае самовывоза) или до покупателя (если заказ доставляет курьер). Формат даты: `ГГГГ-ММ-ДД`.
    - `shipment` — object. Информация об отгрузке.
      - `id` — integer<int64>. Идентификатор отгрузки.
      - `shipmentDate` — string<date> **обязательный**. Дата отгрузки. Формат даты: `ГГГГ-ММ-ДД`.
      - `shipmentTime` — string<time>. Время отгрузки.
    - `courier` — object. Информация о курьерской доставке.
      - `address` — object. Адрес доставки. Указывается, если параметр `type` принимает значение `DELIVERY`, `POST` или `PICKUP` (только для модели DBS). Если `type=PICKUP`, возвращается адрес пункта выдачи.
        - `country` — string. Страна.
        - `postcode` — string. Почтовый индекс.
        - `city` — string. Город или населенный пункт.
        - `district` — string. Район.
        - `subway` — string. Станция метро.
        - `street` — string. Улица.
        - `house` — string. Номер дома.
        - `block` — string. Корпус.
        - `entrance` — string. Номер подъезда.
        - `entryphone` — string. Код домофона.
        - `floor` — string. Этаж.
        - `apartment` — string. Номер квартиры или офиса.
        - `gps` — object. GPS-координаты.
          - `latitude` — number **обязательный**. Широта.
          - `longitude` — number **обязательный**. Долгота.
      - `region` — object. Регион доставки.
        - `id` — integer<int64> **обязательный**. Идентификатор региона.
        - `name` — string **обязательный**. Название региона.
        - `type` — string (OTHER, CONTINENT, REGION, COUNTRY, COUNTRY_DISTRICT, REPUBLIC, CITY, VILLAGE, CITY_DISTRICT, SUBWAY_STATION, REPUBLIC_AREA) **обязательный**. Тип региона.
        - `parent` — object. (циклическая ссылка ./RegionDTO.yaml)
    - `pickup` — object. Информация о доставке в пункт выдачи.
      - `address` — object. Адрес доставки. Указывается, если параметр `type` принимает значение `DELIVERY`, `POST` или `PICKUP` (только для модели DBS). Если `type=PICKUP`, возвращается адрес пункта выдачи.
        - `country` — string. Страна.
        - `postcode` — string. Почтовый индекс.
        - `city` — string. Город или населенный пункт.
        - `district` — string. Район.
        - `subway` — string. Станция метро.
        - `street` — string. Улица.
        - `house` — string. Номер дома.
        - `block` — string. Корпус.
        - `entrance` — string. Номер подъезда.
        - `entryphone` — string. Код домофона.
        - `floor` — string. Этаж.
        - `apartment` — string. Номер квартиры или офиса.
        - `gps` — object. GPS-координаты.
          - `latitude` — number **обязательный**. Широта.
          - `longitude` — number **обязательный**. Долгота.
      - `region` — object. Регион доставки.
        - `id` — integer<int64> **обязательный**. Идентификатор региона.
        - `name` — string **обязательный**. Название региона.
        - `type` — string (OTHER, CONTINENT, REGION, COUNTRY, COUNTRY_DISTRICT, REPUBLIC, CITY, VILLAGE, CITY_DISTRICT, SUBWAY_STATION, REPUBLIC_AREA) **обязательный**. Тип региона.
        - `parent` — object. (циклическая ссылка ./RegionDTO.yaml)
      - `logisticPointId` — integer<int64>. Идентификатор пункта выдачи. Его можно узнать с помощью метода [POST v1/businesses/{businessId}/logistics-points](../../reference/logistic-points/getLogisticPoints.md).
      - `outletCode` — string. Идентификатор пункта самовывоза, присвоенный магазином.
      - `outletStorageLimitDate` — string<date>. Дата, до которой заказ будет храниться в пункте выдачи. Возвращается, когда заказ переходит в статус `PICKUP`. Один раз дату можно поменять с помощью метода [PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/storage-limit](../../reference/order-delivery/updateOrderStorageLimit.md). Формат даты: `ГГГГ-ММ-ДД`.
    - `transfer` — object. Информация о курьере и код подтверждения.
      - `courier` — object. Информация о курьере.
        - `fullName` — string. Полное имя.
        - `phone` — string. Номер телефона.
        - `phoneExtension` — string. Добавочный номер телефона.
        - `vehicleNumber` — string. Номер транспортного средства.
        - `vehicleDescription` — string. Описание транспортного средства. Например, модель и цвет.
      - `eac` — object. Информация о коде подтверждения.
        - `eacType` — string (MERCHANT_TO_COURIER, COURIER_TO_MERCHANT, CHECKING_BY_MERCHANT) **обязательный**. Тип кода подтверждения ЭАПП.
        - `eacCode` — string. Код подтверждения ЭАПП (для типа `MERCHANT_TO_COURIER`).
    - `boxesLayout` — array[object]. Раскладка товаров по коробкам.
      - `items` — array[object] **обязательный**. Список товаров в коробке. Если в коробке едет часть большого товара, в списке может быть только один пункт.
        - `id` — integer<int64> **обязательный**. Идентификатор товара в заказе. Параметр `id` в `items`.
        - `fullCount` — integer<int32>. Количество единиц товара в коробке.
        - `partialCount` — object. Информация о части товара в коробке.
          - `current` — integer<int32> **обязательный**. Номер части, начиная с 1.
          - `total` — integer<int32> **обязательный**. На сколько всего частей разделен товар.
        - `instances` — array[object]. Переданные коды маркировки.
          - `cis` — string. [Код идентификации](*cis-regular-value) единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go). {% note warning "Не экранируйте косую черту в коде символа-разделителя `\u001d`" %} ✅ `01030410947874432155Qbag!\u001d93Zjqw` ❌ `01030410947874432155Qbag!\\u001d93Zjqw` Косые черты и кавычки в других местах экранируйте по правилам JSON: `\\` и `\"` {% endnote %}
          - `uin` — string. Уникальный идентификационный номер ювелирного изделия. Представляет собой число из 16 цифр.
          - `rnpt` — string. Регистрационный номер партии товара. Представляет собой строку из четырех чисел, разделенных косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ/ХХХ. Первая часть — код таможни, которая зарегистрировала декларацию на партию товара. Далее — дата, номер декларации и номер маркированного товара в декларации.
          - `gtd` — string. Грузовая таможенная декларация. Представляет собой строку из трех чисел, разделенных косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ. Первая часть — код таможни, которая зарегистрировала декларацию на ввезенные товары. Далее — дата и номер декларации.
          - `countryCode` — string. Страна производства в формате ISO 3166-1 alpha-2. [Как получить](../../reference/regions/getRegionsCodes.md)
      - `boxId` — integer<int64> **обязательный**. Идентификатор коробки.
      - `barcode` — string **обязательный**. Идентификатор грузового места в системе магазина.
    - `tracks` — array[object]. Информация для отслеживания посылки.
      - `trackCode` — string. Трек‑номер посылки.
      - `deliveryServiceId` — integer<int64> **обязательный**. Идентификатор службы доставки. Информацию о службе доставки можно получить с помощью запроса [GET delivery/services](../../reference/delivery-services/getDeliveryServices.md).
    - `estimated` — boolean. Приблизительная ли дата доставки.
    - `receiveBarcode` — string. **Только для модели LaaS** Штрихкод получения заказа на ПВЗ.
    - `receiveCode` — string. **Только для модели LaaS** Код получения заказа на ПВЗ.
    - `digitalGoods` — object. Информация о доставке цифрового товара.
      - `type` — string (EMAIL, ACTIVATION_CODE, STEAM_GIFT, CHAT) **обязательный**. Тип цифрового товара.
      - `steamLink` — string. Ссылка на Steam-аккаунт покупателя. Передается только для типа `STEAM_GIFT`.
  - `services` — object. Услуги, добавленные в заказ.
    - `liftType` — string (NOT_NEEDED, MANUAL, ELEVATOR, CARGO_ELEVATOR, FREE, UNKNOWN). Тип подъема заказа на этаж: * `NOT_NEEDED` — не требуется. * `MANUAL` — ручной. * `ELEVATOR` — лифт. * `CARGO_ELEVATOR` — грузовой лифт. * `FREE` — любой из перечисленных выше, если включена опция бесплатного подъема. * `UNKNOWN` — неизвестный тип.
  - `buyerType` — string (PERSON, BUSINESS). Тип покупателя: физическое лицо или организация. Только для FBS- и FBY-магазинов, которые размещают товары на витрине [business.market.yandex.ru](https://business.market.yandex.ru).
  - `notes` — string. Комментарий к заказу.
  - `cancelRequested` — boolean. **Только для модели DBS** Запрошена ли отмена.
  - `sourcePlatform` — string (MARKET, OZON, WILDBERRIES, OTHER). Площадка-источник заказа: * `MARKET` — заказ, оформленный на Маркете. * `OTHER` — LaaS-заказ, созданный продавцом.
- `paging` — object. Информация о страницах результатов.
  - `nextPageToken` — string. Идентификатор следующей страницы результатов.

**400** — Запрос содержит неправильные данные. [Подробнее об ошибках при работе с заказами](../../concepts/error-codes#orders)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**401** — В запросе не указаны данные для авторизации. [Подробнее об ошибке](../../concepts/error-codes.md#401)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**403** — Данные для авторизации неверны или доступ к ресурсу запрещен. [Подробнее об ошибке](../../concepts/error-codes.md#403)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**404** — Запрашиваемый ресурс не найден. [Подробнее об ошибке](../../concepts/error-codes.md#404)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**420** — Превышено ограничение на доступ к ресурсу. [Подробнее об ошибке](../../concepts/error-codes.md#420)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**500** — Внутренняя ошибка Маркета. [Подробнее об ошибке](../../concepts/error-codes.md#500)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.
