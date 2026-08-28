---
title: Отчет по счету маркетинга
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMarketingDetalizationReport.md"
fetched_at: "2026-08-28T11:52:59Z"
content_sha: de8847edfa710a7d
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateMarketingDetalizationReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMarketingDetalizationReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateMarketingDetalizationReport.md
  - href: ru/reference/reports/generateMarketingDetalizationReport.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

{% note warning "Структура и содержание отчетов могут изменяться без предварительного уведомления" %}

Например, может добавиться новая колонка или поменяться название листа.

{% endnote %}

<!-- source: ru/api/reports/generateMarketingDetalizationReport.md -->
<div class="openapi">

# Отчет по счету маркетинга

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateMarketingDetalizationReport.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateMarketingDetalizationReport.md -->
  
  Запускает генерацию отчета по счету маркетинга.
  
  Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  <!-- source: ru/_auto/reports/advertiser_billing_operations/advertiser_billing_operations.md -->
  Пояснение к колонкам отчета:

  {% cut "Лист **Полки** (файл **advertiser_operations_shelf**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Буст продаж, оплата за показы** (файл **advertiser_operations_cpm_boost**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Товарные баннеры** (файл **advertiser_operations_product_banners**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Буст продаж, оплата за продажи** (файл **advertiser_operations_cpa_auction_promotion**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Баннеры (бронирование)** (файл **advertiser_operations_package_banners**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Баннеры (аукцион)** (файл **advertiser_operations_auction_banners**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Баннеры кликаут (бронирование)** (файл **advertiser_operations_package_banners_clickout**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Баннеры кликаут (аукцион)** (файл **advertiser_operations_auction_banners_clickout**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Пуши (бронирование)** (файл **advertiser_operations_package_pushes**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Пуши (аукцион)** (файл **advertiser_operations_auction_pushes**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Поп-ап уведомления (бронирование)** (файл **advertiser_operations_package_popups**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Поп-ап уведомления (аукцион)** (файл **advertiser_operations_auction_popups**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Полки с оплатой по дням** (файл **advertiser_operations_cpd_promotion**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Рекламные материалы** (файл **advertiser_operations_marketing_promo_yandex_market**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Реклама на внешних площадках** (файл **advertiser_operations_marketing_promo_web**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Реклама на внешних площадках-М** (файл **advertiser_operations_marketing_promo_web_mark**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **ТВ реклама** (файл **advertiser_operations_marketing_promo_tv**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Рассылка по сегментам** (файл **advertiser_operations_marketing_promo_mailing**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Организация и проведение маркет** (файл **advertiser_operations_marketing_promo_for_sales**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Специальные размещения** (файл **advertiser_operations_marketing_promo_adfox**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Отзывы за баллы** (файл **advertiser_operations_paid_opinion**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || BRAND | brand | Бренд | string ||
  || CATEGORY | category | Категория | string ||
  || MODEL | model | Товар | string ||
  || MARKET_URL | marketUrl | Ссылка на Маркет | string ||
  |#

  {% endcut %}

  {% cut "Лист **Реклама в планшетах (бронирован** (файл **advertiser_operations_package_pads**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Реклама в планшетах (аукцион)** (файл **advertiser_operations_auction_pads**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || SURFACE | surface | Площадки | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Интеграция бренда в Лавке** (файл **advertiser_operations_brand_recommendations_lavka**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Нотификация в Go** (файл **advertiser_operations_notification_go**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Брендинг в Аптеках** (файл **advertiser_operations_branding_pharmacies**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Брендинг в Деливери** (файл **advertiser_operations_branding_delivery**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Брендинг в Еде** (файл **advertiser_operations_branding_eda**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}

  {% cut "Лист **Спецпроекты и интерактивные мех** (файл **advertiser_operations_marketing_special_projects_ultima_eda**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SUM | sum | Сумма (с НДС), ₽ | number ||
  || SERVICE_TYPE | serviceType | Тип услуги | string ||
  || CAMPAIGN_NAME | campaignName | Кампания | string ||
  || OPERATION_TYPE | operationType | Тип операции | string ||
  || CABINET_TYPE | cabinetType | Тип кабинета | string ||
  || CABINET_NAME | cabinetName | Название кабинета | string ||
  |#

  {% endcut %}
  <!-- endsource: ru/_auto/reports/advertiser_billing_operations/advertiser_billing_operations.md -->
  
  <!-- source: ru/_auto/method_limits/generateMarketingDetalizationReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 запрос в 2 минуты<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 запрос в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateMarketingDetalizationReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/businesses/{businessId}/reports/marketing-detalization/generate
  ```
  
  </div>
  
  </div>
  
  </div>
  
  ### Path parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _businessId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор кабинета.
  
  
  Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
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
  ||
  
  _sourceType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SourceType](#entity-SourceType)
  
  Признак типа кабинета, от имени которого вызывается метод:
  
  - `SELLER` — продавец.
  
  
  - `ADVERTISER` — рекламодатель.
  
  
  
  Тип кабинета:
  
  * `SELLER` — продавец.
  * `ADVERTISER` — рекламодатель.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `SELLER`
  
  _Enum:_{.json-schema-reset .json-schema-value} `SELLER`, `ADVERTISER`
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
  
  ### SourceType {#entity-SourceType}
  
  Тип кабинета:
  
  * `SELLER` — продавец.
  * `ADVERTISER` — рекламодатель.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `SELLER`, `ADVERTISER`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "monthOfYear": {
      "year": 2025,
      "month": 12
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _monthOfYear_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ClosureDocumentsMonthOfYearDTO](#entity-ClosureDocumentsMonthOfYearDTO)
  
  Период генерации отчета.
  
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
  pathParams:
    - description: "Идентификатор кабинета.\n\n{% if audience == \"partner\" %}\n\nЧтобы его узнать, воспользуйтесь запросом [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md).\n\nℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)\n\n{% endif %}\n"
      name: businessId
      in: path
      required: true
      schema:
        type: integer
        format: int64
        minimum: 1
  searchParams:
    - description: Формат отчета или документа.
      name: format
      in: query
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/guyl/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportFormatType
    - name: sourceType
      in: query
      required: false
      description: "Признак типа кабинета, от имени которого вызывается метод:\n{% if audience == \"partner\" %}\n\n- `SELLER` — продавец.\n\n{% endif %}\n\n- `ADVERTISER` — рекламодатель.\n\n{% if audience == \"advertiser\" %}\n\n{% note info \"Обязательно указывайте sourceType=ADVERTISER в каждом запросе.\" %}\n\n\_\n\n{% endnote %}\n\n{% endif %}\n"
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/guyl/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/SourceType
        default: SELLER
  headers: []
  body: |-
    {
      "monthOfYear": {
        "year": 2025,
        "month": 12
      }
    }
  schema:
    description: |
      Данные, необходимые для генерации отчета.
    type: object
    required:
      - monthOfYear
    properties:
      monthOfYear:
        description: Период генерации отчета.
        $ref: '#/$defs/ClosureDocumentsMonthOfYearDTO'
    $defs:
      /home/sandbox/.ya/build/build_root/guyl/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ClosureDocumentsMonthOfYearDTO:
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
  path: v1/businesses/{businessId}/reports/marketing-detalization/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateMarketingDetalizationReport.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
