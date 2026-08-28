---
title: Закреплённые отзывы
api: wb-user-communication
tag: pinnedFeedbacks
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
content_sha: 38404034e3396e24
---

# Закреплённые отзывы

Для доступа к методам используйте [токен](./api-information#tag/authorization) для категории Вопросы и отзывы

 Узнать больше о закреплённых отзывах можно в [справочном центре](https://seller.wildberries.ru/instructions/ru/ru/material/pinned-reviews?categoryId=3c971375-9939-45e8-ab82-376019be8942&goBackOption=prevRoute)

С помощью этих методов вы можете:
 1. [Получить список закреплённых и откреплённых отзывов](./user-communication#tag/pinnedFeedbacks/operation/getFeedbacksV1Pins)
 2. [Закрепить отзывы](./user-communication#tag/pinnedFeedbacks/operation/postFeedbacksV1Pins). Метод доступен по [подписке Джем](https://seller.wildberries.ru/monetization/jam) или c [тарифной опцией](https://seller.wildberries.ru/tariff-constructor) **Закрепление отзыва**
 3. [Открепить отзывы](./user-communication#tag/pinnedFeedbacks/operation/deleteFeedbacksV1Pins)
 4. [Получить количество закреплённых и откреплённых отзывов](./user-communication#tag/pinnedFeedbacks/operation/getFeedbacksV1PinsCount)
 5. [Получить лимиты закреплённых отзывов по подписке и тарифной опции](./user-communication#tag/pinnedFeedbacks/operation/getFeedbacksV1PinsLimits)
