---
title: Получение ответов на вопрос
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/goods-questions/answers
operation_id: getGoodsQuestionAnswers
tags:
  - goods-questions
  - fby
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 2f2705edda1e1317
---

# Получение ответов на вопрос

`POST /v1/businesses/{businessId}/goods-questions/answers`

{% include notitle [access](../../_auto/method_scopes/getGoodsQuestionAnswers.md) %}

Возвращает ответы на вопрос о товаре по указанным фильтрам.

{% note tip "Вы также можете настроить API-уведомления" %}

Маркет отправит вам [запрос](../../push-notifications/reference/sendNotification.md), когда появится новый ответ или комментарий. А полную информацию о них можно получить с помощью этого метода.

[{#T}](../../push-notifications/index.md)

{% endnote %}

Результаты возвращаются постранично, одна страница содержит не более 50 ответов.

{% include notitle [limit](../../_auto/method_limits/getGoodsQuestionAnswers.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | — |

## Запрос

**Тело запроса** (`application/json`):

- `questionId` — integer<int64>. Идентификатор вопроса.
- `answerIds` — array[integer<int64>]. Идентификаторы ответов.

## Ответы

**200** — Список ответов на вопрос.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Ответы на вопрос.
  - `answers` — array[object] **обязательный**. Список ответов.
    - `id` — integer<int64> **обязательный**. Идентификатор ответа на вопрос.
    - `text` — string **обязательный**. Текстовое содержимое.
    - `canModify` — boolean **обязательный**. Может ли продавец изменять комментарий или удалять его.
    - `author` — object. Информация об авторе комментария.
      - `type` — string (USER, BUSINESS, VENDOR, BRAND). Тип автора: * `USER` — пользователь. * `BUSINESS` — кабинет. * `VENDOR` — производитель. * `BRAND` — бренд.
      - `name` — string. Имя автора или название кабинета.
    - `status` — string (PUBLISHED, UNMODERATED, BANNED, DELETED) **обязательный**. Статус модерации ответа или комментария: * `PUBLISHED` — опубликован. * `UNMODERATED` — не проверен. * `BANNED` — заблокирован. * `DELETED` — удален.
    - `questionId` — integer<int64> **обязательный**. Идентификатор вопроса.
    - `createdAt` — string<date-time> **обязательный**. Дата и время создания ответа.
    - `votes` — object **обязательный**. Количество лайков и дизлайков на вопросе, ответе или комментарии.
      - `likes` — integer<int64> **обязательный**. Количество лайков.
      - `dislikes` — integer<int64> **обязательный**. Количество дизлайков.
    - `comments` — array[object]. Список комментариев.
      - `id` — integer<int64> **обязательный**. Идентификатор комментария к ответу.
      - `text` — string **обязательный**. Текстовое содержимое.
      - `canModify` — boolean. Может ли продавец изменять комментарий или удалять его.
      - `parentId` — integer<int64>. Идентификатор родительского комментария.
      - `author` — object. Информация об авторе комментария.
        - `type` — string (USER, BUSINESS, VENDOR, BRAND). Тип автора: * `USER` — пользователь. * `BUSINESS` — кабинет. * `VENDOR` — производитель. * `BRAND` — бренд.
        - `name` — string. Имя автора или название кабинета.
      - `status` — string (PUBLISHED, UNMODERATED, BANNED, DELETED) **обязательный**. Статус модерации ответа или комментария: * `PUBLISHED` — опубликован. * `UNMODERATED` — не проверен. * `BANNED` — заблокирован. * `DELETED` — удален.
      - `answerId` — integer<int64> **обязательный**. Идентификатор ответа на вопрос.
      - `createdAt` — string<date-time> **обязательный**. Дата создания комментария.
      - `votes` — object. Количество лайков и дизлайков на вопросе, ответе или комментарии.
        - `likes` — integer<int64> **обязательный**. Количество лайков.
        - `dislikes` — integer<int64> **обязательный**. Количество дизлайков.
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
