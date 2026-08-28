---
title: Управление кампаниями
api: wb-promotion
tag: campaignManagement
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/promotion"
content_sha: fa4d59d7ff75141f
---

# Управление кампаниями

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Продвижение

С помощью методов управления кампаниями вы можете:
 1. [Удалить](./promotion#tag/campaignManagement/operation/getV0Delete) кампанию
 2. [Переименовать](./promotion#tag/campaignManagement/operation/getV0Delete) кампанию
 3. [Запустить](./promotion#tag/campaignManagement/operation/getV0Start) кампанию
 4. [Поставить кампанию на паузу](./promotion#tag/campaignManagement/operation/getV0Pause)
 5. [Завершить](./promotion#tag/campaignManagement/operation/getV0Stop) кампанию
 6. Получить [список рекомендуемых ставок](./promotion#tag/campaignManagement/operation/getV0BidsRecommendations)
 7. Получить [конфигурационные значения продвижения](./promotion#tag/campaignManagement/operation/getV1Config)
 8. Изменить [ставки в кампаниях](./promotion#tag/campaignManagement/operation/patchV1Bids)
 9. Изменить [список карточек товаров в кампаниях](./promotion#tag/campaignManagement/operation/patchV0AuctionNms)
 10. Изменить [места размещения в кампаниях с ручной ставкой](./promotion#tag/campaignManagement/operation/putV0AuctionPlacements)
