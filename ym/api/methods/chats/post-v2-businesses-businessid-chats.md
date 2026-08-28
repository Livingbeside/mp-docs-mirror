---
title: Получение доступных чатов
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/chats
operation_id: getChats
tags:
  - chats
  - dbs
  - fbs
  - fby
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 20e226280f46b5a2
---

# Получение доступных чатов

`POST /v2/businesses/{businessId}/chats`

{% include notitle [access](../../_auto/method_scopes/getChats.md) %} Возвращает чаты с покупателями. {% note tip "Подключите API-уведомления" %} Маркет отправит вам запрос [POST notification](../../push-notifications/reference/sendNotification.md), когда появится новый чат или сообщение. [{#T}](../../push-notifications/index.md) {% endnote %} {% include notitle [limit](../../_auto/method_limits/getChats.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |

## Запрос

**Тело запроса** (`application/json`):

- `orderIds` — array[integer<int64>]. {% note warning "Параметр устарел и будет отключен 19.10.2026." %} Вместо него используйте `contexts`. {% endnote %} Фильтр по идентификаторам заказов на Маркете.
- `contexts` — array[object]. Фильтр по контексту чата.
  - `type` — string (ORDER, RETURN) **обязательный**. Тип чата: * `ORDER` — по заказам. * `RETURN` — по возвратам (FBY, FBS и Экспресс). Подробнее о чатах по заказам и возвратам читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders).
  - `id` — integer<int64> **обязательный**. Идентификатор заказа или возврата.
- `contextTypes` — array[string (ORDER, RETURN, DIRECT)]. Фильтр по типу контекста чата.
- `types` — array[string (CHAT, ARBITRAGE)]. Фильтр по типам чатов.
- `statuses` — array[string (NEW, WAITING_FOR_CUSTOMER, WAITING_FOR_PARTNER, WAITING_FOR_ARBITER, WAITING_FOR_MARKET, FINISHED)]. Фильтр по статусам чатов.

## Ответы

**200** — Список чатов.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Список чатов.
  - `chats` — array[object] **обязательный**. Информация о чатах.
    - `chatId` — integer<int64> **обязательный**. Идентификатор чата.
    - `orderId` — integer<int64>. {% note warning "Параметр устарел и будет отключен 19.10.2026." %} Вместо него используйте `context`. {% endnote %} Идентификатор заказа.
    - `context` — object **обязательный**. Информация о заказе или возврате, по которому начат чат.
      - `type` — string (ORDER, RETURN, DIRECT) **обязательный**. Тип контекста: * `ORDER` — чат по заказу. [Чаты о заказах и возвратах](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders) * `RETURN` — чат по возврату (FBY, FBS и Экспресс). [Чаты о заказах и возвратах](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders) * `DIRECT` — чат, который начал покупатель. [Сообщения от покупателей](https://yandex.ru/support/marketplace/ru/orders/communication/with-users)
      - `customer` — object. Информация о покупателе.
        - `name` — string. Публичное имя покупателя в Яндекс Паспорте, которое отображается в сервисах Яндекса.
        - `publicId` — string. Публичный идентификатор пользователя в Яндекс Паспорте. {% cut "Примеры, где используется" %} * Маркет: `https://market.yandex.ru/user/{public-id}/reviews` * Дзен: `https://zen.yandex.ru/user/{public-id}` * Отзывы: `https://yandex.ru/user/{public-id}` {% endcut %} Подробнее о публичных данных читайте в [документации Яндекс ID](https://yandex.ru/support/id/ru/data/public-data).
      - `campaignId` — integer<int64>. Возвращается для заказов и возвратов.
      - `orderId` — integer<int64>. Идентификатор заказа. Возвращается для заказов и возвратов.
      - `returnId` — integer<int64>. Идентификатор возврата. Возвращается только для возвратов.
    - `type` — string (CHAT, ARBITRAGE) **обязательный**. Тип чата: * `CHAT` — чат с покупателем. * `ARBITRAGE` — спор.
    - `status` — string (NEW, WAITING_FOR_CUSTOMER, WAITING_FOR_PARTNER, WAITING_FOR_ARBITER, WAITING_FOR_MARKET, FINISHED) **обязательный**. Статус чата: * `NEW` — новый чат. * `WAITING_FOR_CUSTOMER` — нужен ответ покупателя. * `WAITING_FOR_PARTNER` — нужен ответ магазина. * `WAITING_FOR_ARBITER` — нужен ответ арбитра. * `WAITING_FOR_MARKET` — нужен ответ Маркета. * `FINISHED` — чат завершен.
    - `createdAt` — string<date-time> **обязательный**. Дата и время создания чата. Формат даты: ISO 8601 со смещением относительно UTC.
    - `updatedAt` — string<date-time> **обязательный**. Дата и время последнего сообщения в чате. Формат даты: ISO 8601 со смещением относительно UTC.
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
