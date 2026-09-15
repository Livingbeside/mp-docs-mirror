---
title: Отчет по схождению с закрывающими документами
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsDetalizationReport.md"
fetched_at: "2026-09-15T02:22:38Z"
content_sha: fb231ba1e4a25fcd
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateClosureDocumentsDetalizationReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsDetalizationReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateClosureDocumentsDetalizationReport.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsDetalizationReport.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

{% note warning "Структура и содержание отчетов могут изменяться без предварительного уведомления" %}

Например, может добавиться новая колонка или поменяться название листа.

{% endnote %}

<!-- source: ru/api/reports/generateClosureDocumentsDetalizationReport.md -->
<div class="openapi">

# Отчет по схождению с закрывающими документами

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateClosureDocumentsDetalizationReport.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateClosureDocumentsDetalizationReport.md -->
  
  Запускает генерацию отчета по схождению с закрывающими документами в зависимости от типа договора.
  
  Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  {% list tabs %}
  
  - Договор на размещение
  
    <!-- source: ru/_auto/reports/period_closure/period_closure_income.md -->
    Пояснение к колонкам отчета:

    {% cut "Лист **Отчёт об исполнении поручения** (файл **period_closure_income_summary**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || PAYMENTS | payments | Платежи по отчёту | string ||
    || PAYMENTS_DESCRIPTION | paymentsDescription | Что это за платежи | string ||
    || PAYMENT_SUM | paymentSum | Сумма платежа* | number ||
    |#

    {% endcut %}

    {% cut "Лист **Получено от потребителей** (файл **period_closure_income_payments**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Возвращено потребителям** (файл **period_closure_income_refunds**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Реализовано от имени заказчика** (файл **period_closure_income_sold_refunds**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Возвращено реализованных** (файл **period_closure_income_sold_defect_refunds**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Удержано за услуги Маркета** (файл **period_closure_income_fees**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Удержано штрафов** (файл **period_closure_income_fines**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Компенсации от Маркета** (файл **period_closure_income_compensations**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Премия** (файл **period_closure_income_netting**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Корректировка Премии** (файл **period_closure_income_premium_correction**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Зачет взаимных обязательств** (файл **period_closure_income_mutual_liabilities**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Приобретено право требования** (файл **period_closure_income_cession**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Списание задолженности** (файл **period_closure_income_debt_write_off**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Подлежит перечислению вам** (файл **period_closure_income_will_be_paid**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Перечислено на ваш счёт** (файл **period_closure_income_paid**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}
    <!-- endsource: ru/_auto/reports/period_closure/period_closure_income.md -->
  
  - Договор на продвижение
  
    <!-- source: ru/_auto/reports/period_closure/period_closure_outcome.md -->
    Пояснение к колонкам отчета:

    {% cut "Лист **Акт об услугах по продвижению** (файл **period_closure_outcome_summary**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || SERVICES | services | Услуги в акте | string ||
    || SERVICES_DESCRIPTION | servicesDescription | Что компенсируется по этой услуге | string ||
    || SERVICES_SUM | servicesSum | Стоимость услуг* | number ||
    |#

    {% endcut %}

    {% cut "Лист **Скидки маркетплейса** (файл **period_closure_outcome_subsidy**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Баллы Яндекс Плюса** (файл **period_closure_outcome_plus**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Премия за выполнение вызова** (файл **period_closure_outcome_benefits**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}

    {% cut "Лист **Скидки маркетплейса на доставку** (файл **period_closure_outcome_delivery**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
    || MODEL | model | Информация о бизнесе/Модели работы | string ||
    || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
    || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
    || INN | inn | Информация о бизнесе/ИНН | string ||
    || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
    || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
    || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
    || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
    || ORDER_ID | orderId | Информация о платежах/Номер заказа или акта об оказанных услугах | integer ||
    || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
    ||
    ORDER_CREATION_DATE
    |
    orderCreationDate
    |
    Информация о платежах/Дата оформления заказа или акта об оказанных услугах
    |
    string
    ||
    || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
    || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
    || OFFER_ID | offerId | Информация о платежах/Ваш SKU | string ||
    || OFFER_NAME | offerName | Информация о платежах/Название товара | string ||
    || COUNT | count | Информация о платежах/Количество, шт. | integer ||
    || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
    || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
    || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
    || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
    || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платёжного поручения | string ||
    || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платёжного поручения | integer ||
    ||
    BANK_ORDER_SUM
    |
    bankOrderSum
    |
    Информация о платежах/Сумма платёжного поручения или удерживаемая за услуги сумма
    |
    number
    ||
    |#

    {% endcut %}
    <!-- endsource: ru/_auto/reports/period_closure/period_closure_outcome.md -->
  
  {% endlist %}
  
  <!-- source: ru/_auto/method_limits/generateClosureDocumentsDetalizationReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 запрос в 2 минуты<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 запрос в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateClosureDocumentsDetalizationReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/reports/closure-documents/detalization/generate
  ```
  
  </div>
  
  </div>
  
  </div>
  
  ### Query parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _format_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReportFormatType](#entity-ReportFormatType)
  
  Формат отчета или документа.
  
  Формат отчета:
  
  * `FILE` — файл с электронной таблицей (XLSX).
  * `CSV` — ZIP-архив с CSV-файлами на каждый лист отчета.
  * `JSON` — ZIP-архив с JSON-файлами на каждый лист отчета.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `FILE`
  
  _Enum:_{.json-schema-reset .json-schema-value} `FILE`, `CSV`, `JSON`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### ReportFormatType {#entity-ReportFormatType}
  
  Формат отчета:
  
  * `FILE` — файл с электронной таблицей (XLSX).
  * `CSV` — ZIP-архив с CSV-файлами на каждый лист отчета.
  * `JSON` — ZIP-архив с JSON-файлами на каждый лист отчета.
  
  
  **Type**: string
  
  _Default:_{.json-schema-reset .json-schema-value} `FILE`
  
  _Enum:_{.json-schema-reset .json-schema-value} `FILE`, `CSV`, `JSON`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "campaignId": 1,
    "monthOfYear": {
      "year": 2025,
      "month": 12
    },
    "contractType": "INCOME"
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CampaignId](#entity-CampaignId)
  
  Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.
  
  Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:
  
  * блок **Идентификатор кампании**;
  * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.
  
  ⚠️ Не путайте его с:
  - идентификатором магазина, который отображается в личном кабинете продавца;
  - рекламными кампаниями.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _contractType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ClosureDocumentsContractType](#entity-ClosureDocumentsContractType)
  
  Тип договора, по которому нужно сгенерировать отчет по схождению с закрывающими документами.
  
  Тип договора:
  
  * `INCOME` — договор на размещение.
  
  * `OUTCOME` — договор на продвижение.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `INCOME`, `OUTCOME`, `MARKETING`
  {.table-cell}
  ||
  ||
  
  _monthOfYear_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ClosureDocumentsMonthOfYearDTO](#entity-ClosureDocumentsMonthOfYearDTO)
  
  Месяц, за который сформированы необходимые закрывающие документы.
  
  Месяц и год.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "year": 2025,
    "month": 12
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CampaignId {#entity-CampaignId}
  
  Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.
  
  Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:
  
  * блок **Идентификатор кампании**;
  * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.
  
  ⚠️ Не путайте его с:
  - идентификатором магазина, который отображается в личном кабинете продавца;
  - рекламными кампаниями.
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Month {#entity-Month}
  
  Номер месяца.
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `12`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ClosureDocumentsMonthOfYearDTO {#entity-ClosureDocumentsMonthOfYearDTO}
  
  Месяц и год.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _month_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [Month](#entity-Month)
  
  Номер месяца.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `12`
  
  _Example:_{.json-schema-reset .json-schema-example} `12`
  {.table-cell}
  ||
  ||
  
  _year_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Год.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "year": 2025,
    "month": 12
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ClosureDocumentsContractType {#entity-ClosureDocumentsContractType}
  
  Тип договора:
  
  * `INCOME` — договор на размещение.
  
  * `OUTCOME` — договор на продвижение.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `INCOME`, `OUTCOME`, `MARKETING`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  В ответ приходит идентификатор, который позволяет узнавать статус генерации и скачать готовый отчет.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "reportId": "example",
      "estimatedGenerationTime": 0
    }
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiResponse](#entity-ApiResponse)
  
    Стандартная обертка для ответов сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _result_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [GenerateReportDTO](#entity-GenerateReportDTO)
  
    Идентификатор, который понадобится для отслеживания статуса генерации и получения готового отчета или документа.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "reportId": "example",
      "estimatedGenerationTime": 0
    }
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "result": {
        "reportId": "example",
        "estimatedGenerationTime": 0
      }
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiResponseStatusType {#entity-ApiResponseStatusType}
  
  Тип ответа.
  Возможные значения:
  * `OK` — ошибок нет.
  * `ERROR` — при обработке запроса произошла ошибка.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `ERROR`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiResponse {#entity-ApiResponse}
  
  Стандартная обертка для ответов сервера.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ApiResponseStatusType](#entity-ApiResponseStatusType)
  
  Тип ответа.
  Возможные значения:
  * `OK` — ошибок нет.
  * `ERROR` — при обработке запроса произошла ошибка.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `ERROR`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "status": "OK"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GenerateReportDTO {#entity-GenerateReportDTO}
  
  Идентификатор, который понадобится для отслеживания статуса генерации и получения готового отчета или документа.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _estimatedGenerationTime_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Ожидаемая продолжительность генерации в миллисекундах.
  {.table-cell}
  ||
  ||
  
  _reportId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Идентификатор, который понадобится для отслеживания статуса генерации и получения готового отчета или документа.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "reportId": "example",
    "estimatedGenerationTime": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__400">
  
  ## 400 Bad Request
  
  Запрос содержит неправильные данные. [Подробнее об ошибках в отчетах и документах](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#reports)
  
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiErrorDTO {#entity-ApiErrorDTO}
  
  Общий формат ошибки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _code_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Код ошибки.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _message_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Описание ошибки.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "code": "example",
    "message": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiErrorResponse {#entity-ApiErrorResponse}
  
  Стандартная обертка для ошибок сервера.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiResponse](#entity-ApiResponse)
  
    Стандартная обертка для ответов сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _errors_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [ApiErrorDTO](#entity-ApiErrorDTO)[] &#124; null
  
    Список ошибок.
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      {
        "code": "example",
        "message": "example"
      }
    ]
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__401">
  
  ## 401 Unauthorized
  
  В запросе не указаны данные для авторизации. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#401)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__403">
  
  ## 403 Forbidden
  
  Данные для авторизации неверны или доступ к ресурсу запрещен. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#403)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__404">
  
  ## 404 Not Found
  
  Запрашиваемый ресурс не найден. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#404)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__420">
  
  ## 420 Method Failure
  
  Превышено ограничение на доступ к ресурсу. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#420)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__500">
  
  ## 500 Internal Server Error
  
  Внутренняя ошибка Маркета. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#500)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
        

- Console

  ```openapi-sandbox translate=no
  pathParams: []
  searchParams:
    - description: Формат отчета или документа.
      name: format
      in: query
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/4tup/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportFormatType
  headers: []
  body: |-
    {
      "campaignId": 1,
      "monthOfYear": {
        "year": 2025,
        "month": 12
      },
      "contractType": "INCOME"
    }
  schema:
    description: |
      Данные, необходимые для генерации отчета.
    type: object
    required:
      - campaignId
      - monthOfYear
      - contractType
    properties:
      campaignId:
        description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
        type: integer
        format: int64
        minimum: 1
      monthOfYear:
        description: Месяц, за который сформированы необходимые закрывающие документы.
        $ref: '#/$defs/ClosureDocumentsMonthOfYearDTO'
      contractType:
        description: >-
          Тип договора, по которому нужно сгенерировать отчет по схождению с
          закрывающими документами.
        $ref: '#/$defs/ClosureDocumentsContractType'
    $defs:
      /home/sandbox/.ya/build/build_root/4tup/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ClosureDocumentsMonthOfYearDTO:
        description: |
          Месяц и год.
        type: object
        required:
          - year
          - month
        properties:
          year:
            description: Год.
            type: integer
            format: int32
            example: 2025
          month:
            description: Номер месяца.
            type: integer
            format: int32
            minimum: 1
            maximum: 12
            example: 12
      /home/sandbox/.ya/build/build_root/4tup/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ClosureDocumentsContractType:
        description: |
          Тип договора:
  
          * `INCOME` — договор на размещение.
  
          * `OUTCOME` — договор на продвижение.
        type: string
        enum:
          - INCOME
          - OUTCOME
          - MARKETING
  bodyType: application/json
  method: post
  security:
    - type: apiKey
      name: Api-Key
      in: header
    - type: oauth2
      x-inline: true
      flows:
        implicit:
          authorizationUrl: https://oauth.yandex.ru/authorize
          scopes:
            market:partner-api: API Яндекс.Маркета / Поиска по товарам для партнеров
  path: v2/reports/closure-documents/detalization/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateClosureDocumentsDetalizationReport.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
