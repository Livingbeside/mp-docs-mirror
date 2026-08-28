---
title: Получение комментариев к отзыву
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/goods-feedback/comments
operation_id: getGoodsFeedbackComments
tags:
  - goods-feedback
  - fby
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: c6f34b05f9a802f3
---

# Получение комментариев к отзыву

`POST /v2/businesses/{businessId}/goods-feedback/comments`

{% include notitle [access](../../_auto/method_scopes/getGoodsFeedbackComments.md) %} Возвращает комментарии к отзыву, кроме: * тех, которые удалили пользователи или Маркет; * комментариев к удаленным отзывам. Идентификатор родительского комментария `parentId` возвращается только для ответов на другие комментарии, но не для ответов на отзывы. {% if audience == "partner" %} {% note tip "Вы также можете настроить API-уведомления" %} Маркет отправит вам [запрос](../../push-notifications/reference/sendNotification.md), когда появится новый комментарий. А полную информацию о нем можно получить с помощью этого метода. [{#T}](../../push-notifications/index.md) {% endnote %} {% endif %} Результаты возвращаются постранично. Комментарии расположены в порядке публикации, поэтому вы можете передавать определенный идентификатор страницы в `pageToken`, если вы получали его ранее. {% include notitle [limit](../../_auto/method_limits/getGoodsFeedbackComments.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |
| `sourceType` | query | string (SELLER, ADVERTISER) | нет | Признак типа кабинета, от имени которого вызывается метод: {% if audience == "partner" %} - `SELLER` — продавец. {% endif %} - `ADVERTISER` — рекламодатель. {% if audience == "advertiser" %} {% note info "Обязательно указывайте sourceType=ADVERTISER в каждом запросе." %} {% endnote %} {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `feedbackId` — integer<int64>. Идентификатор отзыва.
- `commentIds` — array[integer<int64>]. Идентификаторы комментариев. ⚠️ Не используйте это поле одновременно с другими фильтрами. Если вы хотите воспользоваться ими, оставьте поле пустым.

## Ответы

**200** — Дерево комментариев к отзыву.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Комментарии к отзыву.
  - `comments` — array[object] **обязательный**. Список комментариев.
    - `id` — integer<int64> **обязательный**. Идентификатор комментария к отзыву.
    - `text` — string **обязательный**. Текст комментария. Не должен содержать контакты магазина и ссылки на сайты, кроме Маркета.
    - `canModify` — boolean. Может ли продавец изменять комментарий или удалять его.
    - `parentId` — integer<int64>. Идентификатор родительского комментария.
    - `author` — object. Информация об авторе комментария.
      - `type` — string (USER, BUSINESS, BRAND). Тип автора: * `USER` — пользователь. * `BUSINESS` — кабинет. * `BRAND` — бренд.
      - `name` — string. Имя автора или название кабинета.
    - `status` — string (PUBLISHED, UNMODERATED, BANNED, DELETED) **обязательный**. Статус комментария: * `PUBLISHED` — опубликован. * `UNMODERATED` — не проверен. * `BANNED` — заблокирован. * `DELETED` — удален.
    - `feedbackId` — integer<int64> **обязательный**. Идентификатор отзыва.
  - `paging` — object. Идентификатор следующей страницы.
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
