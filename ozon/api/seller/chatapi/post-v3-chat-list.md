---
title: Список чатов
api: ozon-seller
method: POST
path: /v3/chat/list
operation_id: ChatAPI_ChatListV3
tags:
  - ChatAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b81f424351f9f5d6
---

# Список чатов

`POST /v3/chat/list`

Возвращает информацию о чатах по указанным фильтрам.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object. Фильтр по чатам.
  - `chat_status` — string (ALL, OPENED, CLOSED). Фильтр по статусу чата: - `All` — все чаты; - `Opened` — открытые чаты; - `Closed` — закрытые чаты. По умолчанию: `ALL`.
  - `unread_only` — boolean. Фильтр по чатам с непрочитанными сообщениями.
- `limit` — integer<int64> **обязательный**. Количество значений в ответе. Значение по умолчанию — 30. Максимальное значение — 100.
- `cursor` — string. Указатель для выборки следующих данных.

## Ответы

**200** — Список чатов

- `chats` — ?. Данные чатов.
  - `chat` — object. Информация о чате.
    - `created_at` — string<date-time>. Дата создания чата.
    - `chat_id` — string. Идентификатор чата.
    - `chat_status` — string (UNSPECIFIED, OPENED, CLOSED). Статус чата: - `All` — все чаты; - `OPENED` — открытые чаты; - `CLOSED` — закрытые чаты; - `UNSPECIFIED` — не определено. По умолчанию: `UNSPECIFIED`.
    - `chat_type` — string (UNSPECIFIED, SELLER_SUPPORT, BUYER_SELLER, BUYER_SELLER_SELECT, SELLER_API_UPDATES, SELLER_API_NOTIFICATIONS, SELLER_NOTIFICATION_LOGISTICS, SELLER_NOTIFICATION_UPDATE_CONTENT, SELLER_PERSONAL_MANAGER_UNITY_CRM, SELLER_BUSINESS_DEVELOPMENT_GROUP). Тип чата: - `UNSPECIFIED` — не определено; - `SELLER_SUPPORT` — чат с поддержкой; - `BUYER_SELLER` — чат с покупателем; - `BUYER_SELLER_SELECT` — чат с покупателем по заказам Ozon Селект; - `SELLER_API_UPDATES` — чат с обновлениями Seller API; - `SELLER_API_NOTIFICATIONS` — чат с уведомлениями Seller API; - `SELLER_NOTIFICATION_LOGISTICS` — чат с уведомлениями Ozon Доставки; - `SELLER_NOTIFICATION_UPDATE_CONTENT` — чат с уведомлениями об изменениях в атрибутно-категорийной модели; - `SELLER_PERSONAL_MANAGER_UNITY_CRM` — чат с персональным менеджером Ozon; - `SELLER_BUSINESS_DEVELOPMENT_GROUP` — чат с группой бизнес-развития Ozon. По умолчанию: `UNSPECIFIED`.
  - `first_unread_message_id` — integer<uint64>. Идентификатор первого непрочитанного сообщения в чате.
  - `last_message_id` — integer<uint64>. Идентификатор последнего сообщения в чате.
  - `unread_count` — integer<int64>. Количество непрочитанных сообщений в чате.
- `total_unread_count` — integer<int64>. Общее количество непрочитанных сообщений.
- `cursor` — string. Указатель для выборки следующих данных.
- `has_next` — boolean. Признак, что в ответе вернулись не все чаты: - `true` — сделайте повторный запрос с новым параметром `cursor` для получения остальных чатов; - `false` — ответ содержит все чаты для фильтра, который был задан в запросе.

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
