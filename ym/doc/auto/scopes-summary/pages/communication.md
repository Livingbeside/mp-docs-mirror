---
title: Общение с покупателями
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md"
fetched_at: "2026-08-28T11:51:16Z"
content_sha: 983c42828220b592
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/_auto/scopes_summary/pages/communication.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/_auto/scopes_summary/pages/communication.md
  - href: ru/_auto/scopes_summary/pages/communication.md
    type: text/markdown
    title: Markdown version
  - href: ../../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Общение с покупателями

Название доступа в OpenAPI-спецификации: communication.

## Отчеты и документы

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/reports/goods-feedback/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsFeedbackReport.md)
|
Отчет по отзывам о товарах
||
|#

## Отзывы о товарах

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/businesses/{businessId}/goods-feedback](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacks.md)
|
Получение отзывов о товарах продавца
||
||
[POST v1/businesses/{businessId}/goods-feedback-advertiser](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacksUrbanads.md)
|
Получение отзывов о товарах для рекламодателей
||
||
[POST v2/businesses/{businessId}/goods-feedback/comments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbackComments.md)
|
Получение комментариев к отзыву
||
||
[POST v2/businesses/{businessId}/goods-feedback/comments/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md)
|
Добавление нового или изменение созданного комментария
||
||
[POST v2/businesses/{businessId}/goods-feedback/skip-reaction](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/skipGoodsFeedbacksReaction.md)
|
Пропуск реакции на отзывы
||
||
[POST v2/businesses/{businessId}/goods-feedback/comments/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/deleteGoodsFeedbackComment.md)
|
Удаление комментария к отзыву
||
|#

## Вопросы и ответы о товарах

#|
|| **Метод** | **Описание метода** ||
||
[POST v1/businesses/{businessId}/goods-questions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestions.md)
|
Получение вопросов о товарах продавца
||
||
[POST v1/businesses/{businessId}/goods-questions/answers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestionAnswers.md)
|
Получение ответов на вопрос
||
||
[POST v1/businesses/{businessId}/goods-questions/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/updateGoodsQuestionTextEntity.md)
|
Создание, изменение и удаление ответа или комментария
||
|#

## Чаты

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/businesses/{businessId}/chats/history](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatHistory.md)
|
Получение истории сообщений в чате
||
||
[GET v2/businesses/{businessId}/chat](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChat.md)
|
Получение чата по идентификатору
||
||
[POST v2/businesses/{businessId}/chats](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChats.md)
|
Получение доступных чатов
||
||
[GET v2/businesses/{businessId}/chats/message](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatMessage.md)
|
Получение сообщения в чате
||
||
[POST v2/businesses/{businessId}/chats/new](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/createChat.md)
|
Создание нового чата с покупателем
||
||
[POST v2/businesses/{businessId}/chats/message](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/sendMessageToChat.md)
|
Отправка сообщения в чат
||
||
[POST v2/businesses/{businessId}/chats/file/send](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/sendFileToChat.md)
|
Отправка файла в чат
||
|#

## Просмотр дополнительной информации {#common}

#|
|| **Метод** | **Описание метода** ||
|| [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) | Список магазинов пользователя ||
|| [GET v2/campaigns/{campaignId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaign.md) | Информация о магазине ||
||
[POST v2/businesses/{businessId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/businesses/getBusinessSettings.md)
|
Настройки кабинета
||
||
[GET v2/campaigns/{campaignId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md)
|
Настройки магазина
||
|| [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md) | Дерево категорий ||
||
[POST v1/businesses/{businessId}/operations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/operations/getOperations.md)
|
Получение статусов операций
||
||
[GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md)
|
Получение заданного отчета или документа
||
||
[GET v2/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getFulfillmentWarehouses.md)
|
Идентификаторы фулфилмент-складов Маркета
||
||
[POST v2/auth/token](https://yandex.ru/dev/market/partner-api/doc/ru/reference/auth/getAuthTokenInfo.md)
|
Получение информации о токене авторизации
||
||
[GET v2/delivery/services](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-services/getDeliveryServices.md)
|
Справочник служб доставки
||
||
[POST v1/businesses/{businessId}/logistics-points](https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md)
|
Получение точек ПВЗ Маркета
||
||
[POST v2/regions/countries](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/getRegionsCodes.md)
|
Список допустимых кодов стран
||
|| [GET v2/regions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsByName.md) | Поиск регионов по их имени ||
|| [GET v2/regions/{regionId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsById.md) | Информация о регионе ||
||
[GET v2/regions/{regionId}/children](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionChildren.md)
|
Информация о дочерних регионах
||
|#
