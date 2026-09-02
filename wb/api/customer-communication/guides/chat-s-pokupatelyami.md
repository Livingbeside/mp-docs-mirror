---
title: Чат с покупателями
api: wb-customer-communication
tag: buyersChat
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
content_sha: a7a198b61ec50c21
---

# Чат с покупателями

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Чат с покупателями

 Узнать больше о чате с покупателями можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-76?goBackOption=prevRoute&categoryId=62727f31-fac5-477a-9e6e-4789aff9de2e)

Чат позволяет продавцам и покупателям общаться напрямую.

Покупатели могут обращаться с вопросами по товарам или претензиями. Рекомендуем отвечать на сообщения в чате в течение 10 дней.

Чат всегда начинает покупатель. В одном чате можно общаться только с одним покупателем.

 Обработка заявок на возврат товара доступна только в [веб-версии чатов с покупателями](https://seller.wildberries.ru/chat-with-clients).

Работа с чатами:
 1. [Получите список чатов](./user-communication#tag/buyersChat/operation/getV1SellerChats). Сохраните ID чатов в своей базе данных — это позволит обновлять информацию о чатах при получении событий.
 2. [Получите события чатов](./user-communication#tag/buyersChat/operation/getV1SellerEvents): сообщения. У новых чатов значение поля `isNewChat` будет `true`.
 3. [Отправляйте сообщения в чат](./user-communication#tag/buyersChat/operation/postV1SellerMessage)
