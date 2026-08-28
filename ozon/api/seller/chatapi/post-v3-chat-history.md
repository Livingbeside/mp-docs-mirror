---
title: История чата
api: ozon-seller
method: POST
path: /v3/chat/history
operation_id: ChatAPI_ChatHistoryV3
tags:
  - ChatAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 3351c984af20bfee
---

# История чата

`POST /v3/chat/history`

Возвращает историю сообщений чата. По умолчанию от самого нового сообщения к старым. 

 Получите список чатов с покупателем `chats.chat.chat_type="Buyer_Seller"` в ответе метода [/v3/chat/list](#operation/ChatAPI_ChatListV3).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `chat_id` — string **обязательный**. Идентификатор чата.
- `direction` — string. Направление сортировки сообщений: - `Forward` — от старых к новым. - `Backward` — от новых к старым. Значение по умолчанию — `Backward`. Количество сообщений можно установить в параметре `limit`.
- `filter` — object. Фильтр по сообщениям.
  - `message_ids` — array[string<uint64>]. Идентификаторы сообщений.
- `from_message_id` — integer<uint64>. Идентификатор сообщения, с которого нужно начать вывод истории чата. По умолчанию — последнее видимое сообщение. Параметр `from_message_id` обязательный, если `direction = Forward`.
- `limit` — integer<int64>. Количество сообщений в ответе. По умолчанию — 50. Максимальное значение — 1000.

## Ответы

**200** — История чата

- `has_next` — boolean. Признак, что в ответе вернули не все сообщения.
- `messages` — array[object]. Массив сообщений, отсортированный в соответствии с параметром `direction` из тела запроса.
  - `context` — object. Информация о чате.
    - `order_number` — string. Номер заказа.
    - `sku` — string. Идентификатор товара в системе Ozon — SKU.
  - `created_at` — string<date-time>. Дата создания сообщения.
  - `data` — array[string]. Массив с содержимым сообщения в формате Markdown.
  - `is_image` — boolean. Признак, что сообщение содержит изображение.
  - `is_read` — boolean. Признак, что сообщение прочитано.
  - `message_id` — integer<uint64>. Идентификатор сообщения.
  - `moderate_image_status` — string (SUCCESS, MODERATION, FAILED). Статус модерации изображения: - `SUCCESS` — прошло модерацию; - `MODERATION` — на модерации; - `FAILED` — не прошло модерацию.
  - `user` — object. Информация об участнике чата.
    - `id` — string. Идентификатор участника чата.
    - `type` — string. Тип участника чата: - `Customer` — покупатель, - `Seller` — продавец, - `Crm` — системные сообщения, - `Courier` — курьер, - `Support` — поддержка, - `NotificationUser` — уведомления.

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
