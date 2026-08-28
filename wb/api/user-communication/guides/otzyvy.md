---
title: Отзывы
api: wb-user-communication
tag: feedbacks
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
content_sha: c975c39345825f37
---

# Отзывы

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Вопросы и отзывы

 Узнать больше об отзывах можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-79?goBackOption=prevRoute&categoryId=3c971375-9939-45e8-ab82-376019be8942)

Методы для получения отзывов:
 1. [Непросмотренные отзывы и вопросы](./user-communication#tag/questions/operation/getV1NewFeedbacksQuestions)
 2. [Необработанные отзывы](./user-communication#tag/feedbacks/operation/getV1FeedbacksCountUnanswered)
 3. [Количество отзывов](./user-communication#tag/feedbacks/operation/getV1FeedbacksCount)
 4. [Список отзывов](./user-communication#tag/feedbacks/operation/getV1Feedbacks)
 5. [Список архивных отзывов](./user-communication#tag/feedbacks/operation/getV1FeedbacksArchive)

Вы можете получить товар [один отзыв по его ID](./user-communication#tag/feedbacks/operation/getV1Feedback) и работать с полученными вопросами через методы:
 1. [Ответить на отзыв](./user-communication#tag/feedbacks/operation/postV1FeedbacksAnswer)
 1. [Отредактировать ответ на отзыв](./user-communication#tag/feedbacks/operation/patchV1FeedbacksAnswer)
 1. [Возврат товара по ID отзыва](./user-communication#tag/feedbacks/operation/postV1FeedbacksOrderReturn)
