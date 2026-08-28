---
title: Добавление нового или изменение созданного комментария
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/goods-feedback/comments/update
operation_id: updateGoodsFeedbackComment
tags:
  - goods-feedback
  - fby
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: c82419c1e6910e61
---

# Добавление нового или изменение созданного комментария

`POST /v2/businesses/{businessId}/goods-feedback/comments/update`

{% include notitle [access](../../_auto/method_scopes/updateGoodsFeedbackComment.md) %} Добавляет новый комментарий магазина или изменяет комментарий, который магазин оставлял ранее. Для создания комментария к отзыву передайте только идентификатор отзыва `feedbackId`. Чтобы добавить комментарий к другому комментарию, передайте: * `feedbackId` — идентификатор отзыва; * `comment.parentId` — идентификатор родительского комментария. Чтобы изменить комментарий, передайте: * `feedbackId`— идентификатор отзыва; * `comment.id` — идентификатор комментария, который нужно изменить. Если передать одновременно `comment.parentId` и `comment.id`, будет изменен существующий комментарий. {% include notitle [limit](../../_auto/method_limits/updateGoodsFeedbackComment.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `sourceType` | query | string (SELLER, ADVERTISER) | нет | Признак типа кабинета, от имени которого вызывается метод: {% if audience == "partner" %} - `SELLER` — продавец. {% endif %} - `ADVERTISER` — рекламодатель. {% if audience == "advertiser" %} {% note info "Обязательно указывайте sourceType=ADVERTISER в каждом запросе." %} {% endnote %} {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `feedbackId` — integer<int64> **обязательный**. Идентификатор отзыва.
- `comment` — object **обязательный**. Параметры комментария.
  - `id` — integer<int64>. Идентификатор комментария, который нужно изменить. Оставьте поле пустым, если хотите добавить новый комментарий.
  - `parentId` — integer<int64>. Идентификатор родительского комментария, на который нужно ответить.
  - `text` — string **обязательный**. Текст комментария. Не должен содержать контакты магазина и ссылки на сайты, кроме Маркета.

## Ответы

**200** — Информация о добавленном или измененном комментарии.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Комментарий к отзыву.
  - `id` — integer<int64> **обязательный**. Идентификатор комментария к отзыву.
  - `text` — string **обязательный**. Текст комментария. Не должен содержать контакты магазина и ссылки на сайты, кроме Маркета.
  - `canModify` — boolean. Может ли продавец изменять комментарий или удалять его.
  - `parentId` — integer<int64>. Идентификатор родительского комментария.
  - `author` — object. Информация об авторе комментария.
    - `type` — string (USER, BUSINESS, BRAND). Тип автора: * `USER` — пользователь. * `BUSINESS` — кабинет. * `BRAND` — бренд.
    - `name` — string. Имя автора или название кабинета.
  - `status` — string (PUBLISHED, UNMODERATED, BANNED, DELETED) **обязательный**. Статус комментария: * `PUBLISHED` — опубликован. * `UNMODERATED` — не проверен. * `BANNED` — заблокирован. * `DELETED` — удален.
  - `feedbackId` — integer<int64> **обязательный**. Идентификатор отзыва.

**400** — Запрос содержит неправильные данные. [Подробнее об ошибках при работе с отзывами о товарах](../../concepts/error-codes#feedback)

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
