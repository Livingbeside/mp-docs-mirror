---
title: Вопросы
api: wb-customer-communication
tag: questions
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
content_sha: 762e8119e90d1483
---

# Вопросы

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Вопросы и отзывы

 Узнать больше о вопросах можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-81?goBackOption=prevRoute&categoryId=30817062-14cc-4a82-bc78-3600c2b0685b)

Методы для получения вопросов:
 1. [Непросмотренные отзывы и вопросы](./customer-communication#tag/questions/operation/getV1NewFeedbacksQuestions)
 2. [Неотвеченные вопросы](./customer-communication#tag/questions/operation/getV1QuestionsCountUnanswered)
 3. [Количество вопросов](./customer-communication#tag/questions/operation/getV1QuestionsCount)
 4. [Список вопросов](./customer-communication#tag/questions/operation/getV1Questions)

 Вы можете получить [один вопрос по его ID](./customer-communication#tag/questions/operation/getV1Question) и [работать с полученными вопросами](./customer-communication#tag/questions/operation/patchV1Questions).
