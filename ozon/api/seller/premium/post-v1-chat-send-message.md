---
title: Отправить сообщение
api: ozon-seller
method: POST
path: /v1/chat/send/message
operation_id: ChatAPI_ChatSendMessage
tags:
  - Premium
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4b0a8ed78958f7c9
---

# Отправить сообщение

`POST /v1/chat/send/message`

Доступно для продавцов с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro).

Отправляет сообщение в существующий чат по его идентификатору. 

Получите список чатов с покупателем `chats.chat.chat_type="Buyer_Seller"` в ответе метода [/v3/chat/list](#operation/ChatAPI_ChatListV3).

Для отправлений:
- FBO — вы можете отправить сообщение в течение 48 часов с момента получения последнего сообщения от покупателя. 
- FBS или rFBS — вы можете отправить сообщение покупателю после оплаты и в течение 72 часов после доставки отправления. После этого вы можете только отвечать на сообщения в течение 48 часов с момента получения последнего сообщения от покупателя.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `chat_id` — string **обязательный**. Идентификатор чата.
- `text` — string **обязательный**. Текст сообщения в формате plain text от 1 до 1000 символов.

## Ответы

**200** — Сообщение отправлено

- `result` — string. Результат обработки запроса.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
