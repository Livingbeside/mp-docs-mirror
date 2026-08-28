---
title: Общение с покупателями — все методы
api: wb-user-communication
spec_version: communication
operations: 25
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
content_sha: 523669b4dedb62e9
---

# Общение с покупателями

Узнать больше об общении с покупателями можно в справочном центре

С помощью методов общения с покупателями вы можете работать с:
 1. [Вопросами](./user-communication#tag/questions) и [отзывами](./user-communication#tag/feedbacks) покупателей
 2. [Закреплёнными отзывами](./user-communication#tag/pinnedFeedbacks)
 3. [Чатами с покупателями](./user-communication#tag/buyersChat)
 4. [Заявками покупателей на возврат](./user-communication#tag/buyersReturns)

Вы можете протестировать методы общения с покупателями в [песочнице](/sandbox). Также в песочнице доступны [специальные методы](/docs/openapi-other/sandbox-environment#tag/Voprosy-i-otzyvy) для управления тестовыми вопросами и отзывами

 Узнать, как использовать методы в бизнес-кейсах, можно в инструкции по работе с разделом Общение с покупателями

Версия спеки: `communication` · методов: **25**

Источник: https://dev.wildberries.ru/docs/openapi/user-communication

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
