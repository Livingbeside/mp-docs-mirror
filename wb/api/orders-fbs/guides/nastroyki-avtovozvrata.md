---
title: Настройки автовозврата
api: wb-orders-fbs
tag: autoreturnSettings
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
content_sha: e53fbe7b2916c381
---

# Настройки автовозврата

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

С помощью методов этого раздела вы можете управлять [настройками автовозврата](https://seller.wildberries.ru/marketplace-settings) малогабаритных товаров:
 - [получить](./orders-fbs#tag/autoreturnSettings/operation/getMarketplaceV3FbsSettingsAutoreturns) и [обновить](/openapi/orders-fbs#tag/autoreturnSettings/operation/patchMarketplaceV3FbsSettingsAutoreturns) настройки автовозврата продавца
 - [получить](./orders-fbs#tag/autoreturnSettings/operation/postMarketplaceV3FbsSettingsAutoreturnsItems) и [обновить](/openapi/orders-fbs#tag/autoreturnSettings/operation/patchMarketplaceV3FbsSettingsAutoreturnsItems) настройки автовозврата товара
 - получить [список предметов, которые не хранятся на складах WB](/openapi/orders-fbs#tag/autoreturnSettings/operation/getMarketplaceV3FbsSettingsAutoreturnsSubcategoriesRestricted)
