---
title: Получение истории сообщений в чате
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/chats/history
operation_id: getChatHistory
tags:
  - chats
  - dbs
  - fbs
  - fby
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 318c66b12b58a8e4
---

# Получение истории сообщений в чате

`POST /v2/businesses/{businessId}/chats/history`

{% include notitle [access](../../_auto/method_scopes/getChatHistory.md) %} Возвращает историю сообщений в чате с покупателем. {% include notitle [limit](../../_auto/method_limits/getChatHistory.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `chatId` | query | integer<int64> | да | Идентификатор чата. |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |

## Запрос

**Тело запроса** (`application/json`):

- `messageIdFrom` — integer<int64>. Идентификатор сообщения, начиная с которого нужно получить все последующие сообщения.

## Ответы

**200** — История сообщений.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация о сообщениях.
  - `orderId` — integer<int64>. {% note warning "Параметр устарел и будет отключен 12.10.2026." %} Вместо него используйте `context`. {% endnote %} Идентификатор заказа.
  - `context` — object **обязательный**. Информация о заказе или возврате, по которому начат чат.
    - `type` — string (ORDER, RETURN, DIRECT) **обязательный**. Тип контекста: * `ORDER` — чат по заказу. [Чаты о заказах и возвратах](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders) * `RETURN` — чат по возврату (FBY, FBS и Экспресс). [Чаты о заказах и возвратах](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders) * `DIRECT` — чат, который начал покупатель. [Сообщения от покупателей](https://yandex.ru/support/marketplace/ru/orders/communication/with-users)
    - `customer` — object. Информация о покупателе.
      - `name` — string. Публичное имя покупателя в Яндекс Паспорте, которое отображается в сервисах Яндекса.
      - `publicId` — string. Публичный идентификатор пользователя в Яндекс Паспорте. {% cut "Примеры, где используется" %} * Маркет: `https://market.yandex.ru/user/{public-id}/reviews` * Дзен: `https://zen.yandex.ru/user/{public-id}` * Отзывы: `https://yandex.ru/user/{public-id}` {% endcut %} Подробнее о публичных данных читайте в [документации Яндекс ID](https://yandex.ru/support/id/ru/data/public-data).
    - `campaignId` — integer<int64>. Возвращается для заказов и возвратов.
    - `orderId` — integer<int64>. Идентификатор заказа. Возвращается для заказов и возвратов.
    - `returnId` — integer<int64>. Идентификатор возврата. Возвращается только для возвратов.
  - `messages` — array[object] **обязательный**. Информация о сообщениях.
    - `messageId` — integer<int64> **обязательный**. Идентификатор сообщения.
    - `createdAt` — string<date-time> **обязательный**. Дата и время создания сообщения. Формат даты: ISO 8601 со смещением относительно UTC.
    - `sender` — string (PARTNER, CUSTOMER, MARKET, SUPPORT) **обязательный**. Отправитель.
    - `message` — string. Текст сообщения. Необязательный параметр, если возвращается параметр `payload`.
    - `payload` — array[object]. Информация о приложенных к сообщению файлах. Необязательный параметр, если возвращается параметр `message`.
      - `name` — string **обязательный**. Название файла.
      - `url` — string **обязательный**. Ссылка для скачивания файла.
      - `size` — integer<int32> **обязательный**. Размер файла в байтах.
  - `paging` — object. Информация о страницах с результатами.
    - `nextPageToken` — string. Идентификатор следующей страницы результатов.

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
