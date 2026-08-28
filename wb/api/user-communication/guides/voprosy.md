---
title: Вопросы
api: wb-user-communication
tag: questions
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
content_sha: c81a29ec2fce53ba
---

# Вопросы

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Вопросы и отзывы

 Узнать больше о вопросах можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-81?goBackOption=prevRoute&categoryId=30817062-14cc-4a82-bc78-3600c2b0685b)

Методы для получения вопросов:
 1. [Непросмотренные отзывы и вопросы](./user-communication#tag/questions/operation/getV1NewFeedbacksQuestions)
 2. [Неотвеченные вопросы](./user-communication#tag/questions/operation/getV1QuestionsCountUnanswered)
 3. [Количество вопросов](./user-communication#tag/questions/operation/getV1QuestionsCount)
 4. [Список вопросов](./user-communication#tag/questions/operation/getV1Questions)

 Вы можете получить [один вопрос по его ID](./user-communication#tag/questions/operation/getV1Question) и [работать с полученными вопросами](./user-communication#tag/questions/operation/patchV1Questions).
