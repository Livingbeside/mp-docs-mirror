---
title: Получение уведомлений
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md"
fetched_at: "2026-09-26T02:08:22Z"
content_sha: 8b0043bdc81b7dae
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/push-notifications/reference/sendNotification.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/push-notifications/reference/sendNotification.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/pushapi-notification/notification/sendNotification.md -->
<div class="openapi">

# Получение уведомлений

<!-- markdownlint-disable-file -->

Маркет отправляет магазину уведомления о событиях:

  * создание нового заказа;
  * изменение заказа;
  * изменение статуса заказа;
  * создание нового чата с покупателем;
  * добавление нового сообщения в чате;
  * начало спора;
  * завершение спора;
  * создание нового отзыва о товаре;
  * создание нового комментария к отзыву;
  * создание заявки на отмену заказа;
  * отмена заказа;
  * создание нового невыкупа или возврата;
  * изменение статуса невыкупа или возврата.

{% note info "Учитывайте эти особенности в работе с уведомлениями" %}

* Маркет может отправлять несколько уведомлений по одному и тому же событию.

    В некоторых случаях это нормальное поведение. Например, может быть несколько уведомлений с изменением статуса заказа из-за поиска курьера.

* Время в уведомлении, в ответе на запрос к Маркету и в вашей системе может отличаться.

    Это происходит из-за того, что в момент отправки уведомления состояние заказа уже может быть другим.

    В запросе `POST notification` время события приходит в `createdAt`, `updatedAt` или `cancelledAt`. Выбор параметра зависит от типа уведомления.


Актуальным считайте более позднее время события. Оно может быть в уведомлении, вернуться в ответе на запрос к Маркету или храниться в вашей системе.

{% endnote %}

Таймаут на получение ответа: 10 секунд для обычных уведомлений и 1 секунда для проверочного уведомления `PING`.


## Request

<div class="openapi__requests">

<div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">

<div class="openapi__request">

POST {.openapi__method}
```text translate=no
/notification
```

</div>

</div>

</div>

<div class="openapi-entity">

### Body

{% cut "application/json" %}

```json translate=no
{
  "notificationType": "PING",
  "time": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

#|
|| **Name** | **Description** ||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**One of 18 types**" %}{.json-schema-combinators data-marker=or}

- **Type**: [PingNotificationDTO](#entity-PingNotificationDTO)

  Проверочное уведомление.

  `notificationType` = `PING`


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "time": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [OrderCreatedNotificationDTO](#entity-OrderCreatedNotificationDTO)

  Уведомление о создании нового заказа.

  `notificationType` = `ORDER_CREATED`


  {% note tip "Методы, которые могут быть полезны" %}

  [POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md) — передача внешнего идентификатора заказа.

  [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) — получение подробной информации о заказе (по `orderIds`).

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "orderId": 0,
    "campaignId": 1,
    "items": [
      {
        "offerId": "example",
        "count": 0
      }
    ],
    "createdAt": "2025-01-01T00:00:00Z",
    "orderLineServices": [
      {
        "itemId": 1,
        "serviceArticle": "example"
      }
    ]
  }
  ```

  {% endcut %}

- **Type**: [OrderStatusUpdatedNotificationDTO](#entity-OrderStatusUpdatedNotificationDTO)

  Уведомление об изменении статуса заказа.

  `notificationType` = `ORDER_STATUS_UPDATED`

  {% note tip "Чтобы изменить статус заказа" %}

  Используйте метод [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md).

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "orderId": 0,
    "campaignId": 1,
    "status": "PLACING",
    "substatus": "RESERVATION_EXPIRED",
    "updatedAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [OrderCancelledNotificationDTO](#entity-OrderCancelledNotificationDTO)

  Уведомление об отмене заказа.

  `notificationType` = `ORDER_CANCELLED`


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "orderId": 0,
    "campaignId": 1,
    "items": [
      {
        "offerId": "example",
        "count": 0
      }
    ],
    "cancelledAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [OrderCancellationRequestNotificationDTO](#entity-OrderCancellationRequestNotificationDTO)

  Уведомление о создании заявки на отмену заказа (для DBS-магазинов).

  `notificationType` = `ORDER_CANCELLATION_REQUEST`

  Не отправляется, если заказ доставляется в ПВЗ Маркета.

  {% note tip "Чтобы подтвердить или отклонить заявку" %}

  Используйте метод [PUT v2/campaigns/{campaignId}/orders/{orderId}/cancellation/accept](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/acceptOrderCancellation.md).

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "orderId": 0,
    "campaignId": 1,
    "requestedAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [OrderReturnCreatedNotificationDTO](#entity-OrderReturnCreatedNotificationDTO)

  Уведомление о создании нового невыкупа или возврата.

  `notificationType` = `ORDER_RETURN_CREATED`

  {% note tip "Чтобы получить подробную информацию о невыкупе или возврате" %}

  Используйте метод [GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md).

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "orderId": 0,
    "returnId": 0,
    "returnType": "UNREDEEMED",
    "campaignId": 1,
    "items": [
      {
        "offerId": "example",
        "count": 0
      }
    ],
    "createdAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [OrderReturnStatusUpdatedNotificationDTO](#entity-OrderReturnStatusUpdatedNotificationDTO)

  Уведомление о смене статуса невыкупа или возврата.

  `notificationType` = `ORDER_RETURN_STATUS_UPDATED`

  {% note tip "Чтобы получить подробную информацию о невыкупе или возврате" %}

  Используйте метод [GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md).

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "orderId": 0,
    "returnId": 0,
    "campaignId": 1,
    "statuses": {
      "refundStatus": "STARTED_BY_USER",
      "shipmentStatus": "CREATED"
    },
    "updatedAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [OrderUpdatedNotificationDTO](#entity-OrderUpdatedNotificationDTO)

  Уведомление об изменении заказа.

  `notificationType` = `ORDER_UPDATED`

  {% note tip "Чтобы получить подробную информацию о заказе" %}

  Используйте метод [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) с фильтром `orderIds`.

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "orderId": 0,
    "campaignId": 1,
    "updateType": "SHIPMENT_DATE_UPDATED",
    "updatedAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [GoodsFeedbackCreatedNotificationDTO](#entity-GoodsFeedbackCreatedNotificationDTO)

  Уведомление о создании нового отзыва о товаре.

  `notificationType` = `GOODS_FEEDBACK_CREATED`

  Маркет отправляет уведомления об отзывах, только когда они прошли модерацию и опубликованы.

  {% note tip "Чтобы получить подробную информацию об отзывах" %}

  Используйте метод [POST v2/businesses/{businessId}/goods-feedback](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacks.md), где укажите их идентификаторы в параметре `feedbackIds`.

  Получить информацию не получится, если покупатель или Маркет удалил отзыв.

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "feedbackId": 0,
    "businessId": 1,
    "createdAt": "2025-01-01T00:00:00Z",
    "publishedAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [GoodsFeedbackCommentCreatedNotificationDTO](#entity-GoodsFeedbackCommentCreatedNotificationDTO)

  Уведомление о создании нового комментария к отзыву.

  `notificationType` = `GOODS_FEEDBACK_COMMENT_CREATED`

  {% note tip "Чтобы получить подробную информацию о комментариях к отзыву" %}

  Используйте метод [POST v2/businesses/{businessId}/goods-feedback/comments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbackComments.md), где укажите их идентификаторы в параметре `commentIds`.

  Получить информацию не получится, если пользователь или Маркет удалил комментарий или отзыв, к которому он добавлен.

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "commentId": 0,
    "businessId": 1,
    "createdAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [ChatCreatedNotificationDTO](#entity-ChatCreatedNotificationDTO)

  Уведомление о создании нового чата с покупателем.

  `notificationType` = `CHAT_CREATED`

  Приходит для всех типов чатов.

  {% note info "Рекомендуемая обработка" %}

  На уведомление **CHAT_CREATED** создайте чат в своей системе и сохраните `chatId`.

  Получите информацию по чату методом [GET v2/businesses/{businessId}/chat](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChat.md) и сохраните номер заказа, идентификатор возврата (если есть) и публичные данные покупателя.

  Повторно запрашивать контекст чата для данного `chatId` не требуется.

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "chatId": 0,
    "businessId": 1,
    "createdAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [ChatMessageSentNotificationDTO](#entity-ChatMessageSentNotificationDTO)

  Уведомление о новом сообщении в чате.

  `notificationType` = `CHAT_MESSAGE_SENT`

  Приходит для всех типов чатов.

  Не отправляется для сообщений-стикеров.

  {% note tip "Чтобы получить сообщение от покупателя" %}

  Используйте метод [GET v2/businesses/{businessId}/chats/message](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatMessage.md), где укажите идентификаторы:

  * чата — `chatId`;
  * сообщения — `messageId`.

  Если чат уже сохранен (обрабатывали `CHAT_CREATED`) в вашей системе, можно не запрашивать информацию о нем повторно — используйте сохраненный контекст.

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "chatId": 0,
    "messageId": "example",
    "businessId": 1,
    "sentAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [ChatArbitrageStartedNotificationDTO](#entity-ChatArbitrageStartedNotificationDTO)

  Уведомление о начале спора.

  `notificationType` = `CHAT_ARBITRAGE_STARTED`

  Не приходит для чата с типом `DIRECT`. [Подробнее о таких чатах](https://yandex.ru/support/marketplace/ru/orders/communication/with-users)


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "chatId": 0,
    "businessId": 1,
    "startedAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [ChatArbitrageFinishedNotificationDTO](#entity-ChatArbitrageFinishedNotificationDTO)

  Уведомление о завершении спора.

  `notificationType` = `CHAT_ARBITRAGE_FINISHED`

  Не приходит для чата с типом `DIRECT`. [Подробнее о таких чатах](https://yandex.ru/support/marketplace/ru/orders/communication/with-users)


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "chatId": 0,
    "businessId": 1,
    "finishedAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [QuestionCreatedNotificationDTO](#entity-QuestionCreatedNotificationDTO)

  Уведомление о создании нового вопроса.

  `notificationType` = `QUESTION_CREATED`

  {% note tip "Чтобы получить подробную информацию о вопросе" %}

  Используйте метод [POST v1/businesses/{businessId}/goods-questions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestions.md), где укажите его идентификатор в параметре `questionIds`.

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "questionId": 0,
    "businessId": 1,
    "createdAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [QuestionAnswerCreatedNotificationDTO](#entity-QuestionAnswerCreatedNotificationDTO)

  Уведомление о создании нового ответа на вопрос.

  `notificationType` = `QUESTION_ANSWER_CREATED`

  {% note tip "Чтобы получить подробную информацию об ответе на вопрос" %}

  Используйте метод [POST v1/businesses/{businessId}/goods-questions/answers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestionAnswers.md), где укажите его идентификатор в параметре `answerIds`.

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "answerId": 0,
    "businessId": 1,
    "createdAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [QuestionCommentCreatedNotificationDTO](#entity-QuestionCommentCreatedNotificationDTO)

  Уведомление о создании нового комментария к ответу на вопрос.

  `notificationType` = `QUESTION_COMMENT_CREATED`

  {% note tip "Чтобы получить подробную информацию о комментарии к ответу на вопрос" %}

  Используйте метод [POST v1/businesses/{businessId}/goods-questions/answers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestionAnswers.md), где укажите идентификатор ответа в параметре `answerIds`.

  {% endnote %}


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "answerId": 0,
    "commentId": 0,
    "businessId": 1,
    "createdAt": "2025-01-01T00:00:00Z"
  }
  ```

  {% endcut %}

- **Type**: [OrderLineServiceStatusUpdatedNotificationDTO](#entity-OrderLineServiceStatusUpdatedNotificationDTO)

  Уведомление об изменении статуса услуги в заказе.

  `notificationType` = `ORDER_LINE_SERVICE_STATUS_UPDATED`


  {% cut "**Example**" %}{.json-schema-example}

  ```json translate=no
  {
    "notificationType": "PING",
    "orderId": 0,
    "campaignId": 1,
    "itemId": 1,
    "serviceArticle": "example",
    "statuses": [
      {
        "status": "CREATED",
        "count": 0
      }
    ],
    "updatedAt": "2025-01-01T00:00:00Z",
    "cancelReason": "USER_REQUESTED"
  }
  ```

  {% endcut %}

{% endcut %}

</div>

<div class="openapi-entity">

### NotificationType {#entity-NotificationType}

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


**Type**: string

_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`

</div>

<div class="openapi-entity">

### PingNotificationDTO {#entity-PingNotificationDTO}

Проверочное уведомление.

`notificationType` = `PING`


#|
|| **Name** | **Description** ||
||

_notificationType_{.json-schema-reset .json-schema-property}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_time_{.json-schema-reset .json-schema-property}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время обработки уведомления со стороны магазина.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "time": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### CampaignId {#entity-CampaignId}

Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.

Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:

* блок **Идентификатор кампании**;
* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.

⚠️ Не путайте его с:
- идентификатором магазина, который отображается в личном кабинете продавца;
- рекламными кампаниями.


**Type**: integer

_Min value:_{.json-schema-reset .json-schema-assertion} `1`

</div>

<div class="openapi-entity">

### ShopSku {#entity-ShopSku}

Ваш SKU — идентификатор товара в вашей системе.

Правила использования SKU:

* У каждого товара SKU должен быть свой.

* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.

SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).

{% note warning %}

Пробельные символы в начале и конце значения автоматически удаляются. Например, `"  SKU123  "` и `"SKU123"` будут обработаны как одинаковые значения.

{% endnote %}

[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)


**Type**: string

_Min length:_{.json-schema-reset .json-schema-assertion} `1`

_Max length:_{.json-schema-reset .json-schema-assertion} `255`

_Pattern:_{.json-schema-reset .json-schema-assertion} `^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$`

_Example:_{.json-schema-reset .json-schema-example} `example`

</div>

<div class="openapi-entity">

### NotificationOrderItemDTO {#entity-NotificationOrderItemDTO}

Информация о товаре в заказе.

#|
|| **Name** | **Description** ||
||

_count_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Количество товара.
{.table-cell}
||
||

_offerId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [ShopSku](#entity-ShopSku)

Ваш SKU — идентификатор товара в вашей системе.

Правила использования SKU:

* У каждого товара SKU должен быть свой.

* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.

SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).

{% note warning %}

Пробельные символы в начале и конце значения автоматически удаляются. Например, `"  SKU123  "` и `"SKU123"` будут обработаны как одинаковые значения.

{% endnote %}

[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)


_Min length:_{.json-schema-reset .json-schema-assertion} `1`

_Max length:_{.json-schema-reset .json-schema-assertion} `255`

_Pattern:_{.json-schema-reset .json-schema-assertion} `^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$`

_Example:_{.json-schema-reset .json-schema-example} `example`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "offerId": "example",
  "count": 0
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### ItemId {#entity-ItemId}

Идентификатор товара в заказе.

Позволяет идентифицировать товар в рамках заказа.


**Type**: integer

_Min value:_{.json-schema-reset .json-schema-assertion} `1`

</div>

<div class="openapi-entity">

### BusinessOrderLineServiceArticle {#entity-BusinessOrderLineServiceArticle}

Артикул услуги в системе продавца.

Уникальный идентификатор, который продавец задаёт при создании услуги. Используется для всех изменений услуги в рамках заказа.


**Type**: string

_Example:_{.json-schema-reset .json-schema-example} `example`

</div>

<div class="openapi-entity">

### NotificationOrderLineServiceDTO {#entity-NotificationOrderLineServiceDTO}

Информация об услуге в заказе.

#|
|| **Name** | **Description** ||
||

_itemId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [ItemId](#entity-ItemId)

Идентификатор товара в заказе.

Позволяет идентифицировать товар в рамках заказа.


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_serviceArticle_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [BusinessOrderLineServiceArticle](#entity-BusinessOrderLineServiceArticle)

Артикул услуги в системе продавца.

Уникальный идентификатор, который продавец задаёт при создании услуги. Используется для всех изменений услуги в рамках заказа.


_Example:_{.json-schema-reset .json-schema-example} `example`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "itemId": 1,
  "serviceArticle": "example"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### OrderCreatedNotificationDTO {#entity-OrderCreatedNotificationDTO}

Уведомление о создании нового заказа.

`notificationType` = `ORDER_CREATED`


{% note tip "Методы, которые могут быть полезны" %}

[POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md) — передача внешнего идентификатора заказа.

[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) — получение подробной информации о заказе (по `orderIds`).

{% endnote %}


#|
|| **Name** | **Description** ||
||

_campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [CampaignId](#entity-CampaignId)

Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.

Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:

* блок **Идентификатор кампании**;
* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.

⚠️ Не путайте его с:
- идентификатором магазина, который отображается в личном кабинете продавца;
- рекламными кампаниями.


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время создания заказа.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_items_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationOrderItemDTO](#entity-NotificationOrderItemDTO)[]

Список товаров в заказе.

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
[
  {
    "offerId": "example",
    "count": 0
  }
]
```

{% endcut %}
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_orderId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор заказа.
{.table-cell}
||
||

_orderLineServices_{.json-schema-reset .json-schema-property}
{.table-cell}|
**Type**: [NotificationOrderLineServiceDTO](#entity-NotificationOrderLineServiceDTO)[] &#124; null

Список услуг в заказе.

_Min items:_{.json-schema-reset .json-schema-assertion} `1`

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
[
  {
    "itemId": 1,
    "serviceArticle": "example"
  }
]
```

{% endcut %}
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "orderId": 0,
  "campaignId": 1,
  "items": [
    {
      "offerId": "example",
      "count": 0
    }
  ],
  "createdAt": "2025-01-01T00:00:00Z",
  "orderLineServices": [
    {
      "itemId": 1,
      "serviceArticle": "example"
    }
  ]
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### OrderStatusType {#entity-OrderStatusType}

Статус заказа:

* `PLACING` — оформляется, подготовка к резервированию.

* `RESERVED` — зарезервирован, но недооформлен (только для LaaS).

* `UNPAID` — оформлен, но еще не оплачен (если выбрана оплата при оформлении).

* `PROCESSING` — находится в обработке.

* `DELIVERY` — передан в службу доставки.

* `PICKUP` — доставлен в пункт выдачи.

* `DELIVERED` — получен покупателем.

* `CANCELLED` — отменен.

* `PENDING` — ожидает обработки со стороны продавца.

* `PARTIALLY_RETURNED` — возвращен частично.

* `RETURNED` — возвращен полностью.

* `UNKNOWN` — неизвестный статус.

Также могут возвращаться другие значения. Обрабатывать их не нужно.


**Type**: string

_Enum:_{.json-schema-reset .json-schema-value} `PLACING`, `RESERVED`, `UNPAID`, `PROCESSING`, `DELIVERY`, `PICKUP`, `DELIVERED`, `CANCELLED`, `PENDING`, `PARTIALLY_RETURNED`, `RETURNED`, `UNKNOWN`

</div>

<div class="openapi-entity">

### OrderSubstatusType {#entity-OrderSubstatusType}

Этап обработки заказа (статус `PROCESSING`) или причина отмены заказа (статус `CANCELLED`).

* Значения для заказа в статусе `PROCESSING`:

    * `STARTED` — заказ подтвержден, его можно начать обрабатывать.

    * `READY_TO_SHIP` — заказ собран и готов к отправке.

* Значения для заказа в статусе `CANCELLED`:

    * `RESERVATION_EXPIRED` — покупатель не завершил оформление зарезервированного заказа в течение 10 минут.

    * `USER_NOT_PAID` — покупатель не оплатил заказ (для типа оплаты `PREPAID`) в течение 30 минут.

    * `USER_UNREACHABLE` — не удалось связаться с покупателем. Для отмены с этой причиной необходимо выполнить условия:

      * не менее 3 звонков с 8 до 21 в часовом поясе покупателя;
      * перерыв между первым и третьим звонком не менее 90 минут;
      * соединение не короче 5 секунд.

      Если хотя бы одно из этих условий не выполнено (кроме случая, когда номер недоступен), отменить заказ не получится. Вернется ответ с кодом ошибки 400.

    * `USER_CHANGED_MIND` — покупатель отменил заказ по личным причинам.

    * `USER_REFUSED_DELIVERY` — покупателя не устроили условия доставки.

    * `USER_REFUSED_PRODUCT` — покупателю не подошел товар.

    * `SHOP_FAILED` — магазин не может выполнить заказ.

    * `USER_REFUSED_QUALITY` — покупателя не устроило качество товара.

    * `USER_IDENTIFICATION_MISMATCH` — идентификационный документ покупателя не совпадает с данными в заказе.

    * `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED` — заказ участвовал в групповой покупке и был отменен, потому что не было достигнуто нужное количество покупок.

    * `REPLACING_ORDER` — покупатель решил заменить товар другим по собственной инициативе.

    * `PROCESSING_EXPIRED` — значение более не используется.

    * `PICKUP_EXPIRED` — закончился срок хранения заказа в пункт выдачи.

    * `TOO_MANY_DELIVERY_DATE_CHANGES` — заказ переносили слишком много раз.

    * `TOO_LONG_DELIVERY` — заказ доставляется слишком долго.

    * `INCORRECT_PERSONAL_DATA` — для заказа из-за рубежа указаны неправильные данные получателя, заказ не пройдет проверку на таможне.

* `TECHNICAL_ERROR` — техническая ошибка на стороне Маркета. Обратитесь в поддержку.

Также могут возвращаться другие значения. Обрабатывать их не нужно.


**Type**: string

_Enum:_{.json-schema-reset .json-schema-value} `RESERVATION_EXPIRED`, `USER_NOT_PAID`, `USER_UNREACHABLE`, `USER_CHANGED_MIND`, `USER_REFUSED_DELIVERY`, `USER_REFUSED_PRODUCT`, `SHOP_FAILED`, `USER_REFUSED_QUALITY`, `REPLACING_ORDER`, `PROCESSING_EXPIRED`, `PENDING_EXPIRED`, `SHOP_PENDING_CANCELLED`, `PENDING_CANCELLED`, `USER_FRAUD`, `RESERVATION_FAILED`, `USER_PLACED_OTHER_ORDER`, `USER_BOUGHT_CHEAPER`, `MISSING_ITEM`, `BROKEN_ITEM`, `WRONG_ITEM`, `PICKUP_EXPIRED`, `DELIVERY_PROBLEMS`, `LATE_CONTACT`, `CUSTOM`, `DELIVERY_SERVICE_FAILED`, `WAREHOUSE_FAILED_TO_SHIP`, `DELIVERY_SERVICE_UNDELIVERED`, `PREORDER`, `AWAIT_CONFIRMATION`, `STARTED`, `PACKAGING`, `READY_TO_SHIP`, `SHIPPED`, `ASYNC_PROCESSING`, `WAITING_USER_INPUT`, `WAITING_BANK_DECISION`, `BANK_REJECT_CREDIT_OFFER`, `CUSTOMER_REJECT_CREDIT_OFFER`, `CREDIT_OFFER_FAILED`, `AWAIT_DELIVERY_DATES_CONFIRMATION`, `SERVICE_FAULT`, `DELIVERY_SERVICE_RECEIVED`, `USER_RECEIVED`, `WAITING_FOR_STOCKS`, `AS_PART_OF_MULTI_ORDER`, `READY_FOR_LAST_MILE`, `LAST_MILE_STARTED`, `ANTIFRAUD`, `DELIVERY_USER_NOT_RECEIVED`, `DELIVERY_SERVICE_DELIVERED`, `DELIVERED_USER_NOT_RECEIVED`, `USER_WANTED_ANOTHER_PAYMENT_METHOD`, `USER_RECEIVED_TECHNICAL_ERROR`, `USER_FORGOT_TO_USE_BONUS`, `DELIVERY_SERVICE_NOT_RECEIVED`, `DELIVERY_SERVICE_LOST`, `SHIPPED_TO_WRONG_DELIVERY_SERVICE`, `DELIVERED_USER_RECEIVED`, `WAITING_TINKOFF_DECISION`, `COURIER_SEARCH`, `COURIER_FOUND`, `COURIER_IN_TRANSIT_TO_SENDER`, `COURIER_ARRIVED_TO_SENDER`, `COURIER_RECEIVED`, `COURIER_NOT_FOUND`, `COURIER_NOT_DELIVER_ORDER`, `COURIER_RETURNS_ORDER`, `COURIER_RETURNED_ORDER`, `WAITING_USER_DELIVERY_INPUT`, `PICKUP_SERVICE_RECEIVED`, `PICKUP_USER_RECEIVED`, `CANCELLED_COURIER_NOT_FOUND`, `COURIER_NOT_COME_FOR_ORDER`, `DELIVERY_NOT_MANAGED_REGION`, `INCOMPLETE_CONTACT_INFORMATION`, `INCOMPLETE_MULTI_ORDER`, `INAPPROPRIATE_WEIGHT_SIZE`, `TECHNICAL_ERROR`, `SORTING_CENTER_LOST`, `COURIER_SEARCH_NOT_STARTED`, `LOST`, `AWAIT_PAYMENT`, `AWAIT_LAVKA_RESERVATION`, `USER_WANTS_TO_CHANGE_ADDRESS`, `FULL_NOT_RANSOM`, `PRESCRIPTION_MISMATCH`, `DROPOFF_LOST`, `DROPOFF_CLOSED`, `DELIVERY_TO_STORE_STARTED`, `USER_WANTS_TO_CHANGE_DELIVERY_DATE`, `WRONG_ITEM_DELIVERED`, `DAMAGED_BOX`, `AWAIT_DELIVERY_DATES`, `LAST_MILE_COURIER_SEARCH`, `PICKUP_POINT_CLOSED`, `LEGAL_INFO_CHANGED`, `USER_HAS_NO_TIME_TO_PICKUP_ORDER`, `DELIVERY_CUSTOMS_ARRIVED`, `DELIVERY_CUSTOMS_CLEARED`, `FIRST_MILE_DELIVERY_SERVICE_RECEIVED`, `AWAIT_AUTO_DELIVERY_DATES`, `AWAIT_USER_PERSONAL_DATA`, `NO_PERSONAL_DATA_EXPIRED`, `CUSTOMS_PROBLEMS`, `AWAIT_CASHIER`, `WAITING_POSTPAID_BUDGET_RESERVATION`, `AWAIT_SERVICEABLE_CONFIRMATION`, `POSTPAID_BUDGET_RESERVATION_FAILED`, `AWAIT_CUSTOM_PRICE_CONFIRMATION`, `READY_FOR_PICKUP`, `TOO_MANY_DELIVERY_DATE_CHANGES`, `TOO_LONG_DELIVERY`, `DEFERRED_PAYMENT`, `POSTPAID_FAILED`, `INCORRECT_PERSONAL_DATA`, `CUSTOMS_FAILED_MARKET`, `CUSTOMS_FAILED_USER_COMMERCIAL_ITEMS`, `CUSTOMS_FAILED_USER_DUTY_NOT_PAID`, `CUSTOMS_FAILED_USER_INVALID_PERSONAL_DATA`, `CUSTOMS_FAILED_USER_ADDITIONAL_DATA_NOT_PROVIDED`, `AWAIT_PAYMENT_AFTER_DELIVERY`, `AWAIT_USER_STEAM_FAST_URL`, `USER_IDENTIFICATION_MISMATCH`, `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED`, `UNKNOWN`

</div>

<div class="openapi-entity">

### OrderStatusUpdatedNotificationDTO {#entity-OrderStatusUpdatedNotificationDTO}

Уведомление об изменении статуса заказа.

`notificationType` = `ORDER_STATUS_UPDATED`

{% note tip "Чтобы изменить статус заказа" %}

Используйте метод [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md).

{% endnote %}


#|
|| **Name** | **Description** ||
||

_campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [CampaignId](#entity-CampaignId)

Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.

Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:

* блок **Идентификатор кампании**;
* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.

⚠️ Не путайте его с:
- идентификатором магазина, который отображается в личном кабинете продавца;
- рекламными кампаниями.


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_orderId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор заказа.
{.table-cell}
||
||

_status_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [OrderStatusType](#entity-OrderStatusType)

Статус заказа:

* `PLACING` — оформляется, подготовка к резервированию.

* `RESERVED` — зарезервирован, но недооформлен (только для LaaS).

* `UNPAID` — оформлен, но еще не оплачен (если выбрана оплата при оформлении).

* `PROCESSING` — находится в обработке.

* `DELIVERY` — передан в службу доставки.

* `PICKUP` — доставлен в пункт выдачи.

* `DELIVERED` — получен покупателем.

* `CANCELLED` — отменен.

* `PENDING` — ожидает обработки со стороны продавца.

* `PARTIALLY_RETURNED` — возвращен частично.

* `RETURNED` — возвращен полностью.

* `UNKNOWN` — неизвестный статус.

Также могут возвращаться другие значения. Обрабатывать их не нужно.


_Enum:_{.json-schema-reset .json-schema-value} `PLACING`, `RESERVED`, `UNPAID`, `PROCESSING`, `DELIVERY`, `PICKUP`, `DELIVERED`, `CANCELLED`, `PENDING`, `PARTIALLY_RETURNED`, `RETURNED`, `UNKNOWN`
{.table-cell}
||
||

_substatus_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [OrderSubstatusType](#entity-OrderSubstatusType)

Этап обработки заказа (статус `PROCESSING`) или причина отмены заказа (статус `CANCELLED`).

* Значения для заказа в статусе `PROCESSING`:

    * `STARTED` — заказ подтвержден, его можно начать обрабатывать.

    * `READY_TO_SHIP` — заказ собран и готов к отправке.

* Значения для заказа в статусе `CANCELLED`:

    * `RESERVATION_EXPIRED` — покупатель не завершил оформление зарезервированного заказа в течение 10 минут.

    * `USER_NOT_PAID` — покупатель не оплатил заказ (для типа оплаты `PREPAID`) в течение 30 минут.

    * `USER_UNREACHABLE` — не удалось связаться с покупателем. Для отмены с этой причиной необходимо выполнить условия:

      * не менее 3 звонков с 8 до 21 в часовом поясе покупателя;
      * перерыв между первым и третьим звонком не менее 90 минут;
      * соединение не короче 5 секунд.

      Если хотя бы одно из этих условий не выполнено (кроме случая, когда номер недоступен), отменить заказ не получится. Вернется ответ с кодом ошибки 400.

    * `USER_CHANGED_MIND` — покупатель отменил заказ по личным причинам.

    * `USER_REFUSED_DELIVERY` — покупателя не устроили условия доставки.

    * `USER_REFUSED_PRODUCT` — покупателю не подошел товар.

    * `SHOP_FAILED` — магазин не может выполнить заказ.

    * `USER_REFUSED_QUALITY` — покупателя не устроило качество товара.

    * `USER_IDENTIFICATION_MISMATCH` — идентификационный документ покупателя не совпадает с данными в заказе.

    * `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED` — заказ участвовал в групповой покупке и был отменен, потому что не было достигнуто нужное количество покупок.

    * `REPLACING_ORDER` — покупатель решил заменить товар другим по собственной инициативе.

    * `PROCESSING_EXPIRED` — значение более не используется.

    * `PICKUP_EXPIRED` — закончился срок хранения заказа в пункт выдачи.

    * `TOO_MANY_DELIVERY_DATE_CHANGES` — заказ переносили слишком много раз.

    * `TOO_LONG_DELIVERY` — заказ доставляется слишком долго.

    * `INCORRECT_PERSONAL_DATA` — для заказа из-за рубежа указаны неправильные данные получателя, заказ не пройдет проверку на таможне.

* `TECHNICAL_ERROR` — техническая ошибка на стороне Маркета. Обратитесь в поддержку.

Также могут возвращаться другие значения. Обрабатывать их не нужно.


_Enum:_{.json-schema-reset .json-schema-value} `RESERVATION_EXPIRED`, `USER_NOT_PAID`, `USER_UNREACHABLE`, `USER_CHANGED_MIND`, `USER_REFUSED_DELIVERY`, `USER_REFUSED_PRODUCT`, `SHOP_FAILED`, `USER_REFUSED_QUALITY`, `REPLACING_ORDER`, `PROCESSING_EXPIRED`, `PENDING_EXPIRED`, `SHOP_PENDING_CANCELLED`, `PENDING_CANCELLED`, `USER_FRAUD`, `RESERVATION_FAILED`, `USER_PLACED_OTHER_ORDER`, `USER_BOUGHT_CHEAPER`, `MISSING_ITEM`, `BROKEN_ITEM`, `WRONG_ITEM`, `PICKUP_EXPIRED`, `DELIVERY_PROBLEMS`, `LATE_CONTACT`, `CUSTOM`, `DELIVERY_SERVICE_FAILED`, `WAREHOUSE_FAILED_TO_SHIP`, `DELIVERY_SERVICE_UNDELIVERED`, `PREORDER`, `AWAIT_CONFIRMATION`, `STARTED`, `PACKAGING`, `READY_TO_SHIP`, `SHIPPED`, `ASYNC_PROCESSING`, `WAITING_USER_INPUT`, `WAITING_BANK_DECISION`, `BANK_REJECT_CREDIT_OFFER`, `CUSTOMER_REJECT_CREDIT_OFFER`, `CREDIT_OFFER_FAILED`, `AWAIT_DELIVERY_DATES_CONFIRMATION`, `SERVICE_FAULT`, `DELIVERY_SERVICE_RECEIVED`, `USER_RECEIVED`, `WAITING_FOR_STOCKS`, `AS_PART_OF_MULTI_ORDER`, `READY_FOR_LAST_MILE`, `LAST_MILE_STARTED`, `ANTIFRAUD`, `DELIVERY_USER_NOT_RECEIVED`, `DELIVERY_SERVICE_DELIVERED`, `DELIVERED_USER_NOT_RECEIVED`, `USER_WANTED_ANOTHER_PAYMENT_METHOD`, `USER_RECEIVED_TECHNICAL_ERROR`, `USER_FORGOT_TO_USE_BONUS`, `DELIVERY_SERVICE_NOT_RECEIVED`, `DELIVERY_SERVICE_LOST`, `SHIPPED_TO_WRONG_DELIVERY_SERVICE`, `DELIVERED_USER_RECEIVED`, `WAITING_TINKOFF_DECISION`, `COURIER_SEARCH`, `COURIER_FOUND`, `COURIER_IN_TRANSIT_TO_SENDER`, `COURIER_ARRIVED_TO_SENDER`, `COURIER_RECEIVED`, `COURIER_NOT_FOUND`, `COURIER_NOT_DELIVER_ORDER`, `COURIER_RETURNS_ORDER`, `COURIER_RETURNED_ORDER`, `WAITING_USER_DELIVERY_INPUT`, `PICKUP_SERVICE_RECEIVED`, `PICKUP_USER_RECEIVED`, `CANCELLED_COURIER_NOT_FOUND`, `COURIER_NOT_COME_FOR_ORDER`, `DELIVERY_NOT_MANAGED_REGION`, `INCOMPLETE_CONTACT_INFORMATION`, `INCOMPLETE_MULTI_ORDER`, `INAPPROPRIATE_WEIGHT_SIZE`, `TECHNICAL_ERROR`, `SORTING_CENTER_LOST`, `COURIER_SEARCH_NOT_STARTED`, `LOST`, `AWAIT_PAYMENT`, `AWAIT_LAVKA_RESERVATION`, `USER_WANTS_TO_CHANGE_ADDRESS`, `FULL_NOT_RANSOM`, `PRESCRIPTION_MISMATCH`, `DROPOFF_LOST`, `DROPOFF_CLOSED`, `DELIVERY_TO_STORE_STARTED`, `USER_WANTS_TO_CHANGE_DELIVERY_DATE`, `WRONG_ITEM_DELIVERED`, `DAMAGED_BOX`, `AWAIT_DELIVERY_DATES`, `LAST_MILE_COURIER_SEARCH`, `PICKUP_POINT_CLOSED`, `LEGAL_INFO_CHANGED`, `USER_HAS_NO_TIME_TO_PICKUP_ORDER`, `DELIVERY_CUSTOMS_ARRIVED`, `DELIVERY_CUSTOMS_CLEARED`, `FIRST_MILE_DELIVERY_SERVICE_RECEIVED`, `AWAIT_AUTO_DELIVERY_DATES`, `AWAIT_USER_PERSONAL_DATA`, `NO_PERSONAL_DATA_EXPIRED`, `CUSTOMS_PROBLEMS`, `AWAIT_CASHIER`, `WAITING_POSTPAID_BUDGET_RESERVATION`, `AWAIT_SERVICEABLE_CONFIRMATION`, `POSTPAID_BUDGET_RESERVATION_FAILED`, `AWAIT_CUSTOM_PRICE_CONFIRMATION`, `READY_FOR_PICKUP`, `TOO_MANY_DELIVERY_DATE_CHANGES`, `TOO_LONG_DELIVERY`, `DEFERRED_PAYMENT`, `POSTPAID_FAILED`, `INCORRECT_PERSONAL_DATA`, `CUSTOMS_FAILED_MARKET`, `CUSTOMS_FAILED_USER_COMMERCIAL_ITEMS`, `CUSTOMS_FAILED_USER_DUTY_NOT_PAID`, `CUSTOMS_FAILED_USER_INVALID_PERSONAL_DATA`, `CUSTOMS_FAILED_USER_ADDITIONAL_DATA_NOT_PROVIDED`, `AWAIT_PAYMENT_AFTER_DELIVERY`, `AWAIT_USER_STEAM_FAST_URL`, `USER_IDENTIFICATION_MISMATCH`, `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED`, `UNKNOWN`
{.table-cell}
||
||

_updatedAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время изменения статуса заказа.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "orderId": 0,
  "campaignId": 1,
  "status": "PLACING",
  "substatus": "RESERVATION_EXPIRED",
  "updatedAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### OrderCancelledNotificationDTO {#entity-OrderCancelledNotificationDTO}

Уведомление об отмене заказа.

`notificationType` = `ORDER_CANCELLED`


#|
|| **Name** | **Description** ||
||

_campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [CampaignId](#entity-CampaignId)

Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.

Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:

* блок **Идентификатор кампании**;
* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.

⚠️ Не путайте его с:
- идентификатором магазина, который отображается в личном кабинете продавца;
- рекламными кампаниями.


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_cancelledAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время отмены заказа.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_items_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationOrderItemDTO](#entity-NotificationOrderItemDTO)[]

Список товаров в заказе.

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
[
  {
    "offerId": "example",
    "count": 0
  }
]
```

{% endcut %}
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_orderId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор заказа.
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "orderId": 0,
  "campaignId": 1,
  "items": [
    {
      "offerId": "example",
      "count": 0
    }
  ],
  "cancelledAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### OrderCancellationRequestNotificationDTO {#entity-OrderCancellationRequestNotificationDTO}

Уведомление о создании заявки на отмену заказа (для DBS-магазинов).

`notificationType` = `ORDER_CANCELLATION_REQUEST`

Не отправляется, если заказ доставляется в ПВЗ Маркета.

{% note tip "Чтобы подтвердить или отклонить заявку" %}

Используйте метод [PUT v2/campaigns/{campaignId}/orders/{orderId}/cancellation/accept](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/acceptOrderCancellation.md).

{% endnote %}


#|
|| **Name** | **Description** ||
||

_campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [CampaignId](#entity-CampaignId)

Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.

Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:

* блок **Идентификатор кампании**;
* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.

⚠️ Не путайте его с:
- идентификатором магазина, который отображается в личном кабинете продавца;
- рекламными кампаниями.


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_orderId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор заказа.
{.table-cell}
||
||

_requestedAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время создания заявки на отмену заказа.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "orderId": 0,
  "campaignId": 1,
  "requestedAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### ReturnType {#entity-ReturnType}

Тип фильтрации:

* `UNREDEEMED` — невыкупы.

* `RETURN` — возвраты.

Если не указывать, в ответе будут и невыкупы, и возвраты.


**Type**: string

_Enum:_{.json-schema-reset .json-schema-value} `UNREDEEMED`, `RETURN`

</div>

<div class="openapi-entity">

### NotificationReturnItemDTO {#entity-NotificationReturnItemDTO}

Информация о товаре в невыкупе или возврате.

#|
|| **Name** | **Description** ||
||

_count_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Количество товара.
{.table-cell}
||
||

_offerId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [ShopSku](#entity-ShopSku)

Ваш SKU — идентификатор товара в вашей системе.

Правила использования SKU:

* У каждого товара SKU должен быть свой.

* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.

SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).

{% note warning %}

Пробельные символы в начале и конце значения автоматически удаляются. Например, `"  SKU123  "` и `"SKU123"` будут обработаны как одинаковые значения.

{% endnote %}

[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)


_Min length:_{.json-schema-reset .json-schema-assertion} `1`

_Max length:_{.json-schema-reset .json-schema-assertion} `255`

_Pattern:_{.json-schema-reset .json-schema-assertion} `^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$`

_Example:_{.json-schema-reset .json-schema-example} `example`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "offerId": "example",
  "count": 0
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### OrderReturnCreatedNotificationDTO {#entity-OrderReturnCreatedNotificationDTO}

Уведомление о создании нового невыкупа или возврата.

`notificationType` = `ORDER_RETURN_CREATED`

{% note tip "Чтобы получить подробную информацию о невыкупе или возврате" %}

Используйте метод [GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md).

{% endnote %}


#|
|| **Name** | **Description** ||
||

_campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [CampaignId](#entity-CampaignId)

Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.

Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:

* блок **Идентификатор кампании**;
* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.

⚠️ Не путайте его с:
- идентификатором магазина, который отображается в личном кабинете продавца;
- рекламными кампаниями.


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время создания невыкупа или возврата.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_items_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationReturnItemDTO](#entity-NotificationReturnItemDTO)[]

Список товаров в невыкупе или возврате.

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
[
  {
    "offerId": "example",
    "count": 0
  }
]
```

{% endcut %}
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_orderId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор заказа.
{.table-cell}
||
||

_returnId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор невыкупа или возврата.
{.table-cell}
||
||

_returnType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [ReturnType](#entity-ReturnType)

Тип фильтрации:

* `UNREDEEMED` — невыкупы.

* `RETURN` — возвраты.

Если не указывать, в ответе будут и невыкупы, и возвраты.


_Enum:_{.json-schema-reset .json-schema-value} `UNREDEEMED`, `RETURN`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "orderId": 0,
  "returnId": 0,
  "returnType": "UNREDEEMED",
  "campaignId": 1,
  "items": [
    {
      "offerId": "example",
      "count": 0
    }
  ],
  "createdAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### RefundStatusType {#entity-RefundStatusType}

Статус возврата денег:

* `STARTED_BY_USER` — создан покупателем из личного кабинета.

* `REFUND_IN_PROGRESS` — ждет решение о возврате денег (на рассмотрении).

* `REFUNDED` — деньги возвращены.

* `FAILED` — невозможно провести возврат покупателю.

* `WAITING_FOR_DECISION` — ожидает решения (DBS).

* `DECISION_MADE` — по возврату принято решение (DBS).

* `REFUNDED_WITH_BONUSES` — возврат осуществлен баллами Плюса или промокодом.

* `REFUNDED_BY_SHOP` — магазин сделал самостоятельно возврат денег.

* `COMPLETE_WITHOUT_REFUND` — возврат денег не требуется.

* `CANCELLED` — возврат отменен.

* `REJECTED` — возврат отклонен модерацией или в ПВЗ.

* `PREMODERATION_DISPUTE` — по возврату открыт спор (FBY, FBS и Экспресс).

* `PREMODERATION_DECISION_WAITING` — ожидает решения (FBY, FBS и Экспресс).

* `PREMODERATION_DECISION_MADE` — по возврату принято решение (FBY, FBS и Экспресс).

* `PREMODERATION_SELECT_DELIVERY` — пользователь выбирает способ доставки (FBY, FBS и Экспресс).

* `UNKNOWN` — неизвестный статус, обратитесь в поддержку.


**Type**: string

_Enum:_{.json-schema-reset .json-schema-value} `STARTED_BY_USER`, `REFUND_IN_PROGRESS`, `REFUNDED`, `FAILED`, `WAITING_FOR_DECISION`, `DECISION_MADE`, `REFUNDED_WITH_BONUSES`, `REFUNDED_BY_SHOP`, `CANCELLED`, `REJECTED`, `COMPLETE_WITHOUT_REFUND`, `PREMODERATION_DISPUTE`, `PREMODERATION_DECISION_WAITING`, `PREMODERATION_DECISION_MADE`, `PREMODERATION_SELECT_DELIVERY`, `UNKNOWN`

</div>

<div class="openapi-entity">

### ReturnShipmentStatusType {#entity-ReturnShipmentStatusType}

Статус передачи возврата или невыкупа:

* `CREATED` — возврат или невыкуп создан покупателем (оформлен).

* `RECEIVED` — возврат подготовлен к отправке (принят у покупателя).

* `IN_TRANSIT` — возврат или невыкуп в пути (отправлен).

* `READY_FOR_PICKUP` — возврат или невыкуп готов к выдаче магазину.

* `PICKED` — возврат или невыкуп выдан магазину.

* `LOST` — возврат или невыкуп утерян (при транспортировке).

* `EXPIRED` — покупатель не принес товар на возврат вовремя (возврат отменен).

* `CANCELLED` — возврат или невыкуп отменен.

* `FULFILMENT_RECEIVED` — возврат или невыкуп принят на складе Маркета.

* `PREPARED_FOR_UTILIZATION` — возврат или невыкуп передан в очередь на утилизацию.

* `NOT_IN_DEMAND` — возврат или невыкуп не забрали с почты.

* `UTILIZED` — возврат или невыкуп утилизирован.

* `READY_FOR_EXPROPRIATION` — товары в возврате или невыкупе направлены на перепродажу (проверка перед реализацией).

* `RECEIVED_FOR_EXPROPRIATION` — товары в возврате или невыкупе приняты для перепродажи (реализация).

* `UNKNOWN` — неизвестный статус, обратитесь в поддержку.


**Type**: string

_Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `RECEIVED`, `IN_TRANSIT`, `READY_FOR_PICKUP`, `PICKED`, `LOST`, `EXPIRED`, `CANCELLED`, `FULFILMENT_RECEIVED`, `PREPARED_FOR_UTILIZATION`, `NOT_IN_DEMAND`, `UTILIZED`, `READY_FOR_EXPROPRIATION`, `RECEIVED_FOR_EXPROPRIATION`, `UNKNOWN`

</div>

<div class="openapi-entity">

### NotificationUpdatedReturnStatusesDTO {#entity-NotificationUpdatedReturnStatusesDTO}

Информация об обновлении статуса невыкупа или возврата.

Возвращается только тот статус, который был изменен.

Для невыкупов приходит только `shipmentStatus`.

Параметр `shipmentStatus` не приходит для возвратов с опцией **Быстрый возврат денег за дешевый брак**, когда товар остается у покупателя.


#|
|| **Name** | **Description** ||
||

_refundStatus_{.json-schema-reset .json-schema-property}
{.table-cell}|
**Type**: [RefundStatusType](#entity-RefundStatusType)

Статус возврата денег:

* `STARTED_BY_USER` — создан покупателем из личного кабинета.

* `REFUND_IN_PROGRESS` — ждет решение о возврате денег (на рассмотрении).

* `REFUNDED` — деньги возвращены.

* `FAILED` — невозможно провести возврат покупателю.

* `WAITING_FOR_DECISION` — ожидает решения (DBS).

* `DECISION_MADE` — по возврату принято решение (DBS).

* `REFUNDED_WITH_BONUSES` — возврат осуществлен баллами Плюса или промокодом.

* `REFUNDED_BY_SHOP` — магазин сделал самостоятельно возврат денег.

* `COMPLETE_WITHOUT_REFUND` — возврат денег не требуется.

* `CANCELLED` — возврат отменен.

* `REJECTED` — возврат отклонен модерацией или в ПВЗ.

* `PREMODERATION_DISPUTE` — по возврату открыт спор (FBY, FBS и Экспресс).

* `PREMODERATION_DECISION_WAITING` — ожидает решения (FBY, FBS и Экспресс).

* `PREMODERATION_DECISION_MADE` — по возврату принято решение (FBY, FBS и Экспресс).

* `PREMODERATION_SELECT_DELIVERY` — пользователь выбирает способ доставки (FBY, FBS и Экспресс).

* `UNKNOWN` — неизвестный статус, обратитесь в поддержку.


_Enum:_{.json-schema-reset .json-schema-value} `STARTED_BY_USER`, `REFUND_IN_PROGRESS`, `REFUNDED`, `FAILED`, `WAITING_FOR_DECISION`, `DECISION_MADE`, `REFUNDED_WITH_BONUSES`, `REFUNDED_BY_SHOP`, `CANCELLED`, `REJECTED`, `COMPLETE_WITHOUT_REFUND`, `PREMODERATION_DISPUTE`, `PREMODERATION_DECISION_WAITING`, `PREMODERATION_DECISION_MADE`, `PREMODERATION_SELECT_DELIVERY`, `UNKNOWN`
{.table-cell}
||
||

_shipmentStatus_{.json-schema-reset .json-schema-property}
{.table-cell}|
**Type**: [ReturnShipmentStatusType](#entity-ReturnShipmentStatusType)

Статус передачи возврата или невыкупа:

* `CREATED` — возврат или невыкуп создан покупателем (оформлен).

* `RECEIVED` — возврат подготовлен к отправке (принят у покупателя).

* `IN_TRANSIT` — возврат или невыкуп в пути (отправлен).

* `READY_FOR_PICKUP` — возврат или невыкуп готов к выдаче магазину.

* `PICKED` — возврат или невыкуп выдан магазину.

* `LOST` — возврат или невыкуп утерян (при транспортировке).

* `EXPIRED` — покупатель не принес товар на возврат вовремя (возврат отменен).

* `CANCELLED` — возврат или невыкуп отменен.

* `FULFILMENT_RECEIVED` — возврат или невыкуп принят на складе Маркета.

* `PREPARED_FOR_UTILIZATION` — возврат или невыкуп передан в очередь на утилизацию.

* `NOT_IN_DEMAND` — возврат или невыкуп не забрали с почты.

* `UTILIZED` — возврат или невыкуп утилизирован.

* `READY_FOR_EXPROPRIATION` — товары в возврате или невыкупе направлены на перепродажу (проверка перед реализацией).

* `RECEIVED_FOR_EXPROPRIATION` — товары в возврате или невыкупе приняты для перепродажи (реализация).

* `UNKNOWN` — неизвестный статус, обратитесь в поддержку.


_Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `RECEIVED`, `IN_TRANSIT`, `READY_FOR_PICKUP`, `PICKED`, `LOST`, `EXPIRED`, `CANCELLED`, `FULFILMENT_RECEIVED`, `PREPARED_FOR_UTILIZATION`, `NOT_IN_DEMAND`, `UTILIZED`, `READY_FOR_EXPROPRIATION`, `RECEIVED_FOR_EXPROPRIATION`, `UNKNOWN`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "refundStatus": "STARTED_BY_USER",
  "shipmentStatus": "CREATED"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### OrderReturnStatusUpdatedNotificationDTO {#entity-OrderReturnStatusUpdatedNotificationDTO}

Уведомление о смене статуса невыкупа или возврата.

`notificationType` = `ORDER_RETURN_STATUS_UPDATED`

{% note tip "Чтобы получить подробную информацию о невыкупе или возврате" %}

Используйте метод [GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md).

{% endnote %}


#|
|| **Name** | **Description** ||
||

_campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [CampaignId](#entity-CampaignId)

Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.

Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:

* блок **Идентификатор кампании**;
* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.

⚠️ Не путайте его с:
- идентификатором магазина, который отображается в личном кабинете продавца;
- рекламными кампаниями.


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_orderId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор заказа.
{.table-cell}
||
||

_returnId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор невыкупа или возврата.
{.table-cell}
||
||

_statuses_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationUpdatedReturnStatusesDTO](#entity-NotificationUpdatedReturnStatusesDTO)

Информация об обновлении статуса невыкупа или возврата.

Возвращается только тот статус, который был изменен.

Для невыкупов приходит только `shipmentStatus`.

Параметр `shipmentStatus` не приходит для возвратов с опцией **Быстрый возврат денег за дешевый брак**, когда товар остается у покупателя.


{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "refundStatus": "STARTED_BY_USER",
  "shipmentStatus": "CREATED"
}
```

{% endcut %}
{.table-cell}
||
||

_updatedAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время изменения статуса невыкупа или возврата.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "orderId": 0,
  "returnId": 0,
  "campaignId": 1,
  "statuses": {
    "refundStatus": "STARTED_BY_USER",
    "shipmentStatus": "CREATED"
  },
  "updatedAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### OrderUpdateType {#entity-OrderUpdateType}

Тип изменения заказа:

* `SHIPMENT_DATE_UPDATED` — изменение даты отгрузки.
* `DELIVERY_DATE_UPDATED` — изменение даты доставки.
* `UNKNOWN` — неизвестный тип.


**Type**: string

_Enum:_{.json-schema-reset .json-schema-value} `SHIPMENT_DATE_UPDATED`, `DELIVERY_DATE_UPDATED`, `UNKNOWN`

</div>

<div class="openapi-entity">

### OrderUpdatedNotificationDTO {#entity-OrderUpdatedNotificationDTO}

Уведомление об изменении заказа.

`notificationType` = `ORDER_UPDATED`

{% note tip "Чтобы получить подробную информацию о заказе" %}

Используйте метод [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) с фильтром `orderIds`.

{% endnote %}


#|
|| **Name** | **Description** ||
||

_campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [CampaignId](#entity-CampaignId)

Идентификатор кампании.

Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.

Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:

* блок **Идентификатор кампании**;
* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.

⚠️ Не путайте его с:
- идентификатором магазина, который отображается в личном кабинете продавца;
- рекламными кампаниями.


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_orderId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор заказа.
{.table-cell}
||
||

_updatedAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время изменения заказа.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_updateType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [OrderUpdateType](#entity-OrderUpdateType)

Тип изменения заказа.

Тип изменения заказа:

* `SHIPMENT_DATE_UPDATED` — изменение даты отгрузки.
* `DELIVERY_DATE_UPDATED` — изменение даты доставки.
* `UNKNOWN` — неизвестный тип.


_Enum:_{.json-schema-reset .json-schema-value} `SHIPMENT_DATE_UPDATED`, `DELIVERY_DATE_UPDATED`, `UNKNOWN`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "orderId": 0,
  "campaignId": 1,
  "updateType": "SHIPMENT_DATE_UPDATED",
  "updatedAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### GoodsFeedbackId {#entity-GoodsFeedbackId}

Идентификатор отзыва.


**Type**: integer

</div>

<div class="openapi-entity">

### BusinessId {#entity-BusinessId}

Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).

ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)


**Type**: integer

_Min value:_{.json-schema-reset .json-schema-assertion} `1`

</div>

<div class="openapi-entity">

### GoodsFeedbackCreatedNotificationDTO {#entity-GoodsFeedbackCreatedNotificationDTO}

Уведомление о создании нового отзыва о товаре.

`notificationType` = `GOODS_FEEDBACK_CREATED`

Маркет отправляет уведомления об отзывах, только когда они прошли модерацию и опубликованы.

{% note tip "Чтобы получить подробную информацию об отзывах" %}

Используйте метод [POST v2/businesses/{businessId}/goods-feedback](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacks.md), где укажите их идентификаторы в параметре `feedbackIds`.

Получить информацию не получится, если покупатель или Маркет удалил отзыв.

{% endnote %}


#|
|| **Name** | **Description** ||
||

_businessId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [BusinessId](#entity-BusinessId)

Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).

ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время создания отзыва.

Может отличаться от информации в `publishedAt`, так как некоторое время отзыв проходит модерацию.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_feedbackId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [GoodsFeedbackId](#entity-GoodsFeedbackId)

Идентификатор отзыва.


_Example:_{.json-schema-reset .json-schema-example} `0`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_publishedAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время публикации отзыва.

Может отличаться от информации в `createdAt`, так как некоторое время отзыв проходит модерацию.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "feedbackId": 0,
  "businessId": 1,
  "createdAt": "2025-01-01T00:00:00Z",
  "publishedAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### GoodsFeedbackCommentId {#entity-GoodsFeedbackCommentId}

Идентификатор комментария к отзыву.


**Type**: integer

</div>

<div class="openapi-entity">

### GoodsFeedbackCommentCreatedNotificationDTO {#entity-GoodsFeedbackCommentCreatedNotificationDTO}

Уведомление о создании нового комментария к отзыву.

`notificationType` = `GOODS_FEEDBACK_COMMENT_CREATED`

{% note tip "Чтобы получить подробную информацию о комментариях к отзыву" %}

Используйте метод [POST v2/businesses/{businessId}/goods-feedback/comments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbackComments.md), где укажите их идентификаторы в параметре `commentIds`.

Получить информацию не получится, если пользователь или Маркет удалил комментарий или отзыв, к которому он добавлен.

{% endnote %}


#|
|| **Name** | **Description** ||
||

_businessId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [BusinessId](#entity-BusinessId)

Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).

ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_commentId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [GoodsFeedbackCommentId](#entity-GoodsFeedbackCommentId)

Идентификатор комментария к отзыву.


_Example:_{.json-schema-reset .json-schema-example} `0`
{.table-cell}
||
||

_createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время создания комментария.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "commentId": 0,
  "businessId": 1,
  "createdAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### ChatCreatedNotificationDTO {#entity-ChatCreatedNotificationDTO}

Уведомление о создании нового чата с покупателем.

`notificationType` = `CHAT_CREATED`

Приходит для всех типов чатов.

{% note info "Рекомендуемая обработка" %}

На уведомление **CHAT_CREATED** создайте чат в своей системе и сохраните `chatId`.

Получите информацию по чату методом [GET v2/businesses/{businessId}/chat](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChat.md) и сохраните номер заказа, идентификатор возврата (если есть) и публичные данные покупателя.

Повторно запрашивать контекст чата для данного `chatId` не требуется.

{% endnote %}


#|
|| **Name** | **Description** ||
||

_businessId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [BusinessId](#entity-BusinessId)

Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).

ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_chatId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор чата.
{.table-cell}
||
||

_createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время создания чата.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "chatId": 0,
  "businessId": 1,
  "createdAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### ChatMessageSentNotificationDTO {#entity-ChatMessageSentNotificationDTO}

Уведомление о новом сообщении в чате.

`notificationType` = `CHAT_MESSAGE_SENT`

Приходит для всех типов чатов.

Не отправляется для сообщений-стикеров.

{% note tip "Чтобы получить сообщение от покупателя" %}

Используйте метод [GET v2/businesses/{businessId}/chats/message](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatMessage.md), где укажите идентификаторы:

* чата — `chatId`;
* сообщения — `messageId`.

Если чат уже сохранен (обрабатывали `CHAT_CREATED`) в вашей системе, можно не запрашивать информацию о нем повторно — используйте сохраненный контекст.

{% endnote %}


#|
|| **Name** | **Description** ||
||

_businessId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [BusinessId](#entity-BusinessId)

Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).

ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_chatId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор чата.
{.table-cell}
||
||

_messageId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string

Идентификатор сообщения.

_Example:_{.json-schema-reset .json-schema-example} `example`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_sentAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время отправки сообщения.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "chatId": 0,
  "messageId": "example",
  "businessId": 1,
  "sentAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### ChatArbitrageStartedNotificationDTO {#entity-ChatArbitrageStartedNotificationDTO}

Уведомление о начале спора.

`notificationType` = `CHAT_ARBITRAGE_STARTED`

Не приходит для чата с типом `DIRECT`. [Подробнее о таких чатах](https://yandex.ru/support/marketplace/ru/orders/communication/with-users)


#|
|| **Name** | **Description** ||
||

_businessId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [BusinessId](#entity-BusinessId)

Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).

ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_chatId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор чата.
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_startedAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время начала спора.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "chatId": 0,
  "businessId": 1,
  "startedAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### ChatArbitrageFinishedNotificationDTO {#entity-ChatArbitrageFinishedNotificationDTO}

Уведомление о завершении спора.

`notificationType` = `CHAT_ARBITRAGE_FINISHED`

Не приходит для чата с типом `DIRECT`. [Подробнее о таких чатах](https://yandex.ru/support/marketplace/ru/orders/communication/with-users)


#|
|| **Name** | **Description** ||
||

_businessId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [BusinessId](#entity-BusinessId)

Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).

ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_chatId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор чата.
{.table-cell}
||
||

_finishedAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время завершения спора.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "chatId": 0,
  "businessId": 1,
  "finishedAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### QuestionCreatedNotificationDTO {#entity-QuestionCreatedNotificationDTO}

Уведомление о создании нового вопроса.

`notificationType` = `QUESTION_CREATED`

{% note tip "Чтобы получить подробную информацию о вопросе" %}

Используйте метод [POST v1/businesses/{businessId}/goods-questions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestions.md), где укажите его идентификатор в параметре `questionIds`.

{% endnote %}


#|
|| **Name** | **Description** ||
||

_businessId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [BusinessId](#entity-BusinessId)

Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).

ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время создания вопроса.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_questionId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор вопроса.
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "questionId": 0,
  "businessId": 1,
  "createdAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### QuestionAnswerCreatedNotificationDTO {#entity-QuestionAnswerCreatedNotificationDTO}

Уведомление о создании нового ответа на вопрос.

`notificationType` = `QUESTION_ANSWER_CREATED`

{% note tip "Чтобы получить подробную информацию об ответе на вопрос" %}

Используйте метод [POST v1/businesses/{businessId}/goods-questions/answers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestionAnswers.md), где укажите его идентификатор в параметре `answerIds`.

{% endnote %}


#|
|| **Name** | **Description** ||
||

_answerId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор ответа.
{.table-cell}
||
||

_businessId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [BusinessId](#entity-BusinessId)

Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).

ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время создания ответа.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "answerId": 0,
  "businessId": 1,
  "createdAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### QuestionCommentCreatedNotificationDTO {#entity-QuestionCommentCreatedNotificationDTO}

Уведомление о создании нового комментария к ответу на вопрос.

`notificationType` = `QUESTION_COMMENT_CREATED`

{% note tip "Чтобы получить подробную информацию о комментарии к ответу на вопрос" %}

Используйте метод [POST v1/businesses/{businessId}/goods-questions/answers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestionAnswers.md), где укажите идентификатор ответа в параметре `answerIds`.

{% endnote %}


#|
|| **Name** | **Description** ||
||

_answerId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор ответа.
{.table-cell}
||
||

_businessId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [BusinessId](#entity-BusinessId)

Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).

ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_commentId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор комментария.
{.table-cell}
||
||

_createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время создания комментария.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "answerId": 0,
  "commentId": 0,
  "businessId": 1,
  "createdAt": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### OrderLineServiceStatusType {#entity-OrderLineServiceStatusType}

Статус оказания услуги:

* `CREATED` — услуга создана, но ещё не оказана.
* `PROVIDED` — услуга оказана.
* `CANCELLED` — услуга отменена.


**Type**: string

_Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `PROVIDED`, `CANCELLED`

</div>

<div class="openapi-entity">

### NotificationOrderLineServiceStatusDTO {#entity-NotificationOrderLineServiceStatusDTO}

Количество единиц услуги в указанном статусе.

#|
|| **Name** | **Description** ||
||

_count_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Количество единиц услуги в статусе.
{.table-cell}
||
||

_status_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [OrderLineServiceStatusType](#entity-OrderLineServiceStatusType)

Статус оказания услуги:

* `CREATED` — услуга создана, но ещё не оказана.
* `PROVIDED` — услуга оказана.
* `CANCELLED` — услуга отменена.


_Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `PROVIDED`, `CANCELLED`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "status": "CREATED",
  "count": 0
}
```

{% endcut %}

</div>

<div class="openapi-entity">

### OrderLineServiceCancelReasonType {#entity-OrderLineServiceCancelReasonType}

Причина отмены услуги:

* `USER_REQUESTED` — покупатель попросил отменить услугу.
* `SHOP_UNABLE_TO_RENDER` — магазин не может оказать услугу.
* `USER_UNREACHABLE` — не удалось связаться с покупателем.
* `UNKNOWN` — неизвестная причина.


**Type**: string

_Enum:_{.json-schema-reset .json-schema-value} `USER_REQUESTED`, `SHOP_UNABLE_TO_RENDER`, `USER_UNREACHABLE`, `UNKNOWN`

</div>

<div class="openapi-entity">

### OrderLineServiceStatusUpdatedNotificationDTO {#entity-OrderLineServiceStatusUpdatedNotificationDTO}

Уведомление об изменении статуса услуги в заказе.

`notificationType` = `ORDER_LINE_SERVICE_STATUS_UPDATED`


#|
|| **Name** | **Description** ||
||

_campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [CampaignId](#entity-CampaignId)

Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.

Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:

* блок **Идентификатор кампании**;
* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.

⚠️ Не путайте его с:
- идентификатором магазина, который отображается в личном кабинете продавца;
- рекламными кампаниями.


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_itemId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [ItemId](#entity-ItemId)

Идентификатор товара в заказе.

Позволяет идентифицировать товар в рамках заказа.


_Min value:_{.json-schema-reset .json-schema-assertion} `1`

_Example:_{.json-schema-reset .json-schema-example} `1`
{.table-cell}
||
||

_notificationType_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationType](#entity-NotificationType)

Тип уведомления:

* `PING` — проверочное уведомление.
* `ORDER_CREATED` — создан новый заказ.
* `ORDER_CANCELLED` — заказ отменен.
* `ORDER_STATUS_UPDATED` — статус заказа изменен.
* `ORDER_RETURN_CREATED` — создан новый невыкуп или возврат.
* `ORDER_CANCELLATION_REQUEST` — создана заявка на отмену заказа (для DBS-магазинов).
* `ORDER_RETURN_STATUS_UPDATED` — статус невыкупа или возврата изменен.
* `ORDER_UPDATED` — заказ изменен.
* `ORDER_LINE_SERVICE_STATUS_UPDATED` — изменен статус услуги в заказе.
* `GOODS_FEEDBACK_CREATED` — создан новый отзыв о товаре.
* `GOODS_FEEDBACK_COMMENT_CREATED` — создан новый комментарий к отзыву о товаре.
* `CHAT_CREATED` — создан новый чат с покупателем.
* `CHAT_MESSAGE_SENT` — добавлено новое сообщение в чате.
* `CHAT_ARBITRAGE_STARTED` — по обращению покупателя начался спор.
* `CHAT_ARBITRAGE_FINISHED` — спор завершен.
* `QUESTION_CREATED` — создан новый вопрос.
* `QUESTION_ANSWER_CREATED` — создан новый ответ на вопрос.
* `QUESTION_COMMENT_CREATED` — создан новый комментарий к ответу на вопрос.


_Enum:_{.json-schema-reset .json-schema-value} `PING`, `ORDER_CREATED`, `ORDER_CANCELLED`, `ORDER_STATUS_UPDATED`, `ORDER_RETURN_CREATED`, `ORDER_CANCELLATION_REQUEST`, `ORDER_RETURN_STATUS_UPDATED`, `ORDER_UPDATED`, `ORDER_LINE_SERVICE_STATUS_UPDATED`, `GOODS_FEEDBACK_CREATED`, `GOODS_FEEDBACK_COMMENT_CREATED`, `CHAT_CREATED`, `CHAT_MESSAGE_SENT`, `CHAT_ARBITRAGE_STARTED`, `CHAT_ARBITRAGE_FINISHED`, `QUESTION_CREATED`, `QUESTION_ANSWER_CREATED`, `QUESTION_COMMENT_CREATED`
{.table-cell}
||
||

_orderId_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: integer

Идентификатор заказа.
{.table-cell}
||
||

_serviceArticle_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [BusinessOrderLineServiceArticle](#entity-BusinessOrderLineServiceArticle)

Артикул услуги в системе продавца.

Уникальный идентификатор, который продавец задаёт при создании услуги. Используется для всех изменений услуги в рамках заказа.


_Example:_{.json-schema-reset .json-schema-example} `example`
{.table-cell}
||
||

_statuses_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: [NotificationOrderLineServiceStatusDTO](#entity-NotificationOrderLineServiceStatusDTO)[]

Разбивка единиц услуги по статусам после изменения.

_Min items:_{.json-schema-reset .json-schema-assertion} `1`

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
[
  {
    "status": "CREATED",
    "count": 0
  }
]
```

{% endcut %}
{.table-cell}
||
||

_updatedAt_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время последнего изменения статуса услуги.

Формат даты: ISO 8601 со смещением относительно UTC. Например, `2017-11-21T00:00:00.213Z`.


_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_cancelReason_{.json-schema-reset .json-schema-property}
{.table-cell}|
**Type**: [OrderLineServiceCancelReasonType](#entity-OrderLineServiceCancelReasonType)

Причина отмены услуги:

* `USER_REQUESTED` — покупатель попросил отменить услугу.
* `SHOP_UNABLE_TO_RENDER` — магазин не может оказать услугу.
* `USER_UNREACHABLE` — не удалось связаться с покупателем.
* `UNKNOWN` — неизвестная причина.


_Enum:_{.json-schema-reset .json-schema-value} `USER_REQUESTED`, `SHOP_UNABLE_TO_RENDER`, `USER_UNREACHABLE`, `UNKNOWN`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "notificationType": "PING",
  "orderId": 0,
  "campaignId": 1,
  "itemId": 1,
  "serviceArticle": "example",
  "statuses": [
    {
      "status": "CREATED",
      "count": 0
    }
  ],
  "updatedAt": "2025-01-01T00:00:00Z",
  "cancelReason": "USER_REQUESTED"
}
```

{% endcut %}

</div>

## Responses

<div class="openapi__response__code__200">

## 200 OK

Ответ на корректный запрос с информацией об обработке уведомления.

<div class="openapi-entity">

### Body

{% cut "application/json" %}

```json translate=no
{
  "version": "example",
  "name": "example",
  "time": "2025-01-01T00:00:00Z"
}
```

{% endcut %}

#|
|| **Name** | **Description** ||
||

_name_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string

Название интеграции.

_Min length:_{.json-schema-reset .json-schema-assertion} `1`

_Max length:_{.json-schema-reset .json-schema-assertion} `100`

_Example:_{.json-schema-reset .json-schema-example} `example`
{.table-cell}
||
||

_time_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string&lt;date-time&gt;

Дата и время начала обработки уведомления в формате UTC.

_Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
{.table-cell}
||
||

_version_{.json-schema-reset .json-schema-property .json-schema-required}
{.table-cell}|
**Type**: string

Версия интеграции.

_Min length:_{.json-schema-reset .json-schema-assertion} `1`

_Max length:_{.json-schema-reset .json-schema-assertion} `100`

_Example:_{.json-schema-reset .json-schema-example} `example`
{.table-cell}
||
|#{.json-schema-properties}

</div>

</div>

<div class="openapi__response__code__400">

## 400 Bad Request

Если Маркет прислал некорректное уведомление, верните статус `400` с описанием ошибки.

<div class="openapi-entity">

### Body

{% cut "application/json" %}

```json translate=no
{
  "error": {
    "type": "UNKNOWN",
    "message": "example"
  }
}
```

{% endcut %}

#|
|| **Name** | **Description** ||
||

_error_{.json-schema-reset .json-schema-property}
{.table-cell}|
**Type**: [NotificationApiErrorDTO](#entity-NotificationApiErrorDTO)

Ошибка при обработке уведомления.

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "type": "UNKNOWN",
  "message": "example"
}
```

{% endcut %}
{.table-cell}
||
|#{.json-schema-properties}

</div>

<div class="openapi-entity">

### NotificationApiErrorType {#entity-NotificationApiErrorType}

Тип ошибки:

* `UNKNOWN` — неизвестная ошибка.
* `WRONG_EVENT_FORMAT` — неправильный тип уведомления.
* `DUPLICATED_EVENT` — дублирующее уведомление.


**Type**: string

_Enum:_{.json-schema-reset .json-schema-value} `UNKNOWN`, `WRONG_EVENT_FORMAT`, `DUPLICATED_EVENT`

</div>

<div class="openapi-entity">

### NotificationApiErrorDTO {#entity-NotificationApiErrorDTO}

Ошибка при обработке уведомления.

#|
|| **Name** | **Description** ||
||

_message_{.json-schema-reset .json-schema-property}
{.table-cell}|
**Type**: string

Описание ошибки.

_Example:_{.json-schema-reset .json-schema-example} `example`
{.table-cell}
||
||

_type_{.json-schema-reset .json-schema-property}
{.table-cell}|
**Type**: [NotificationApiErrorType](#entity-NotificationApiErrorType)

Тип ошибки:

* `UNKNOWN` — неизвестная ошибка.
* `WRONG_EVENT_FORMAT` — неправильный тип уведомления.
* `DUPLICATED_EVENT` — дублирующее уведомление.


_Enum:_{.json-schema-reset .json-schema-value} `UNKNOWN`, `WRONG_EVENT_FORMAT`, `DUPLICATED_EVENT`
{.table-cell}
||
|#{.json-schema-properties}

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "type": "UNKNOWN",
  "message": "example"
}
```

{% endcut %}

</div>

</div>

<div class="openapi__response__code__500">

## 500 Internal Server Error

Если произошла техническая ошибка на вашей стороне, верните статус `500`. [API магазина не отвечает](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md#no-answer)

<div class="openapi-entity">

### Body

{% cut "application/json" %}

```json translate=no
{
  "error": {
    "type": "UNKNOWN",
    "message": "example"
  }
}
```

{% endcut %}

#|
|| **Name** | **Description** ||
||

_error_{.json-schema-reset .json-schema-property}
{.table-cell}|
**Type**: [NotificationApiErrorDTO](#entity-NotificationApiErrorDTO)

Ошибка при обработке уведомления.

{% cut "**Example**" %}{.json-schema-example}

```json translate=no
{
  "type": "UNKNOWN",
  "message": "example"
}
```

{% endcut %}
{.table-cell}
||
|#{.json-schema-properties}

</div>

</div>

</div>
<!-- endsource: ru/pushapi-notification/notification/sendNotification.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
