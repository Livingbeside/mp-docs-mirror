---
title: Общение с покупателями — все методы
api: wb-customer-communication
spec_version: communication
operations: 25
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
content_sha: cdf716001f4c2774
---

# Общение с покупателями

Узнать больше об общении с покупателями можно в [справочном центре](https://seller.wildberries.ru/instructions/category/f7f6c465-dd12-422d-80a0-a6d9562115d5?goBackOption=prevRoute&categoryId=30817062-14cc-4a82-bc78-3600c2b0685b)

С помощью методов общения с покупателями вы можете работать с:
 1. [Вопросами](./customer-communication#tag/questions) и [отзывами](./customer-communication#tag/feedbacks) покупателей
 2. [Закреплёнными отзывами](./customer-communication#tag/pinnedFeedbacks)
 3. [Чатами с покупателями](./customer-communication#tag/buyersChat)
 4. [Заявками покупателей на возврат](./customer-communication#tag/buyersReturns)

Вы можете протестировать методы общения с покупателями в [песочнице](/sandbox). Также в песочнице доступны [специальные методы](/docs/openapi-other/sandbox-environment#tag/questionsAndFeedbacks) для управления тестовыми вопросами и отзывами

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-0b26-7620-8d0b-e3050b7cd01d/obshchenie-s-pokupateliami) по работе с разделом Общение с покупателями

Версия спеки: `communication` · методов: **25** · разделов справки: **6**

Источник: https://dev.wildberries.ru/docs/openapi/customer-communication

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `DELETE` | `/api/feedbacks/v1/pins` | pinnedFeedbacks | [Открепить отзывы](pinnedfeedbacks/delete-api-feedbacks-v1-pins.md) |
| `GET` | `/api/feedbacks/v1/pins/count` | pinnedFeedbacks | [Количество закреплённых и откреплённых отзывов](pinnedfeedbacks/get-api-feedbacks-v1-pins-count.md) |
| `GET` | `/api/feedbacks/v1/pins/limits` | pinnedFeedbacks | [Лимиты закреплённых отзывов](pinnedfeedbacks/get-api-feedbacks-v1-pins-limits.md) |
| `GET` | `/api/feedbacks/v1/pins` | pinnedFeedbacks | [Список закреплённых и откреплённых отзывов](pinnedfeedbacks/get-api-feedbacks-v1-pins.md) |
| `GET` | `/api/v1/claims` | buyersReturns | [Заявки покупателей на возврат](buyersreturns/get-api-v1-claims.md) |
| `GET` | `/api/v1/feedback` | feedbacks | [Получить отзыв по ID](feedbacks/get-api-v1-feedback.md) |
| `GET` | `/api/v1/feedbacks/archive` | feedbacks | [Список архивных отзывов](feedbacks/get-api-v1-feedbacks-archive.md) |
| `GET` | `/api/v1/feedbacks/count-unanswered` | feedbacks | [Необработанные отзывы](feedbacks/get-api-v1-feedbacks-count-unanswered.md) |
| `GET` | `/api/v1/feedbacks/count` | feedbacks | [Количество отзывов](feedbacks/get-api-v1-feedbacks-count.md) |
| `GET` | `/api/v1/feedbacks` | feedbacks | [Список отзывов](feedbacks/get-api-v1-feedbacks.md) |
| `GET` | `/api/v1/new-feedbacks-questions` | questions | [Непросмотренные отзывы и вопросы](questions/get-api-v1-new-feedbacks-questions.md) |
| `GET` | `/api/v1/question` | questions | [Получить вопрос по ID](questions/get-api-v1-question.md) |
| `GET` | `/api/v1/questions/count-unanswered` | questions | [Неотвеченные вопросы](questions/get-api-v1-questions-count-unanswered.md) |
| `GET` | `/api/v1/questions/count` | questions | [Количество вопросов](questions/get-api-v1-questions-count.md) |
| `GET` | `/api/v1/questions` | questions | [Список вопросов](questions/get-api-v1-questions.md) |
| `GET` | `/api/v1/seller/chats` | buyersChat | [Список чатов](buyerschat/get-api-v1-seller-chats.md) |
| `GET` | `/api/v1/seller/download/{id}` | buyersChat | [Получить файл из сообщения{{ /api/v1/seller/download/{id} }}](buyerschat/get-api-v1-seller-download-id.md) |
| `GET` | `/api/v1/seller/events` | buyersChat | [События чатов](buyerschat/get-api-v1-seller-events.md) |
| `PATCH` | `/api/v1/claim` | buyersReturns | [Ответ на заявку покупателя](buyersreturns/patch-api-v1-claim.md) |
| `PATCH` | `/api/v1/feedbacks/answer` | feedbacks | [Отредактировать ответ на отзыв](feedbacks/patch-api-v1-feedbacks-answer.md) |
| `PATCH` | `/api/v1/questions` | questions | [Работа с вопросами](questions/patch-api-v1-questions.md) |
| `POST` | `/api/feedbacks/v1/pins` | pinnedFeedbacks | [Закрепить отзывы](pinnedfeedbacks/post-api-feedbacks-v1-pins.md) |
| `POST` | `/api/v1/feedbacks/answer` | feedbacks | [Ответить на отзыв](feedbacks/post-api-v1-feedbacks-answer.md) |
| `POST` | `/api/v1/feedbacks/order/return` | feedbacks | [Возврат товара по ID отзыва](feedbacks/post-api-v1-feedbacks-order-return.md) |
| `POST` | `/api/v1/seller/message` | buyersChat | [Отправить сообщение](buyerschat/post-api-v1-seller-message.md) |
