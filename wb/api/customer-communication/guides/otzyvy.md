---
title: Отзывы
api: wb-customer-communication
tag: feedbacks
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
content_sha: 1632f5e61837748d
---

# Отзывы

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Вопросы и отзывы

 Узнать больше об отзывах можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-79?goBackOption=prevRoute&categoryId=3c971375-9939-45e8-ab82-376019be8942)

Методы для получения отзывов:
 1. [Непросмотренные отзывы и вопросы](./customer-communication#tag/questions/operation/getV1NewFeedbacksQuestions)
 2. [Необработанные отзывы](./customer-communication#tag/feedbacks/operation/getV1FeedbacksCountUnanswered)
 3. [Количество отзывов](./customer-communication#tag/feedbacks/operation/getV1FeedbacksCount)
 4. [Список отзывов](./customer-communication#tag/feedbacks/operation/getV1Feedbacks)
 5. [Список архивных отзывов](./customer-communication#tag/feedbacks/operation/getV1FeedbacksArchive)

Вы можете получить товар [один отзыв по его ID](./customer-communication#tag/feedbacks/operation/getV1Feedback) и работать с полученными вопросами через методы:
 1. [Ответить на отзыв](./customer-communication#tag/feedbacks/operation/postV1FeedbacksAnswer)
 1. [Отредактировать ответ на отзыв](./customer-communication#tag/feedbacks/operation/patchV1FeedbacksAnswer)
 1. [Возврат товара по ID отзыва](./customer-communication#tag/feedbacks/operation/postV1FeedbacksOrderReturn)
