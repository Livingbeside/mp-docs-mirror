---
title: Получение сообщения в чате
api: yandex-market
method: GET
path: /v2/businesses/{businessId}/chats/message
operation_id: getChatMessage
tags:
  - chats
  - dbs
  - fbs
  - fby
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: a294738f3980c471
---

# Получение сообщения в чате

`GET /v2/businesses/{businessId}/chats/message`

{% include notitle [access](../../_auto/method_scopes/getChatMessage.md) %}

Возвращает сообщение по его идентификатору.

{% note tip "Подключите API-уведомления" %}

Маркет отправит вам запрос [POST notification](../../push-notifications/reference/sendNotification.md), когда появится новый чат или сообщение.

[{#T}](../../push-notifications/index.md)

{% endnote %}

{% include notitle [limit](../../_auto/method_limits/getChatMessage.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `chatId` | query | integer<int64> | да | Идентификатор чата. |
| `messageId` | query | integer<int64> | да | Идентификатор сообщения. |

## Ответы

**200** — Сообщение и информация о нем.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация о сообщении.
  - `messageId` — integer<int64> **обязательный**. Идентификатор сообщения.
  - `createdAt` — string<date-time> **обязательный**. Дата и время создания сообщения. Формат даты: ISO 8601 со смещением относительно UTC.
  - `sender` — string (PARTNER, CUSTOMER, MARKET, SUPPORT) **обязательный**. Отправитель.
  - `message` — string. Текст сообщения. Необязательный параметр, если возвращается параметр `payload`.
  - `payload` — array[object]. Информация о приложенных к сообщению файлах. Необязательный параметр, если возвращается параметр `message`.
    - `name` — string **обязательный**. Название файла.
    - `url` — string **обязательный**. Ссылка для скачивания файла.
    - `size` — integer<int32> **обязательный**. Размер файла в байтах.

**400** — Запрос содержит неправильные данные. [Подробнее об ошибке](../../concepts/error-codes.md#400)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**401** — В запросе не указаны данные для авторизации. [Подробнее об ошибке](../../concepts/error-codes.md#401)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**403** — Данные для авторизации неверны или доступ к ресурсу запрещен. [Подробнее об ошибке](../../concepts/error-codes.md#403)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**404** — Запрашиваемый ресурс не найден. [Подробнее об ошибке](../../concepts/error-codes.md#404)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**420** — Превышено ограничение на доступ к ресурсу. [Подробнее об ошибке](../../concepts/error-codes.md#420)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**500** — Внутренняя ошибка Маркета. [Подробнее об ошибке](../../concepts/error-codes.md#500)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.
