---
title: Подключить URL-адрес для уведомлений
api: ozon-seller
method: POST
path: /v1/notification/set
operation_id: SetNotification
tags:
  - Notification
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d9f4a44ea0931b63
---

# Подключить URL-адрес для уведомлений

`POST /v1/notification/set`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1978-Novye-beta-metody-dlia-upravleniia-podkliucheniiami-PUSH-uvedomlenii/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `types` — array[string (TYPE_NEW_MESSAGE, TYPE_UPDATE_MESSAGE, TYPE_MESSAGE_READ, TYPE_CHAT_CLOSED, TYPE_NEW_POSTING, TYPE_POSTING_CANCELLED, TYPE_STATE_CHANGED, TYPE_DELIVERY_DATE_CHANGED, TYPE_CUTOFF_DATE_CHANGED, TYPE_CREATE_ITEM, TYPE_UPDATE_ITEM, TYPE_CREATE_OR_UPDATE_ITEM…)] **обязательный**. Типы уведомлений: - `TYPE_NEW_MESSAGE` — новое сообщение в чате; - `TYPE_UPDATE_MESSAGE` — изменение сообщения в чате; - `TYPE_MESSAGE_READ` — ваше сообщение прочитано покупателем или поддержкой; - `TYPE_CHAT_CLOSED` — чат закрыт; - `TYPE_NEW_POSTING` — новое отправление; - `TYPE_POSTING_CANCELLED` — отмена отправления; - `TYPE_STATE_CHANGED` — изменение статуса отправления; - `TYPE_DELIVERY_DATE_CHANGED` — изменение даты доставки отправления; - `TYPE_CUTOFF_DATE_CHANGED` — изменение даты отгрузки отправления; - `TYPE_CREATE_ITEM` — создание товара или ошибка при его создании; - `TYPE_UPDATE_ITEM` — обновление товара или ошибка при обновлении; - `TYPE_CREATE_OR_UPDATE_ITEM` — создание и обновление товара или ошибка в процессе; - `TYPE_STOCKS_CHANGED` — изменение остатков на складах продавца; - `TYPE_FBO_POSTING_NEW` — новое отправление FBO; - `TYPE_FBO_POSTING_CANCELLED` — отмена отправления FBO; - `TYPE_FBO_POSTING_STATE_CHANGED` — изменение статуса отправления FBO; - `TYPE_FBO_POSTING_DELIVERY_DATE_CHANGED` — изменение даты доставки отправления FBO; - `TYPE_FBO_STOCKS_CHANGED` — изменение остатков на складах Ozon; - `TYPE_ORDER_NEW` — новый заказ; - `TYPE_ORDER_CANCELLED` — отмена заказа; - `TYPE_ORDER_STATE_CHANGED` — изменение статуса заказа.
- `url` — string **обязательный**. URL-адрес.

## Ответы

**200** — URL-адрес подключён

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
