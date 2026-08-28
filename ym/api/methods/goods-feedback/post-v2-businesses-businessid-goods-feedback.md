---
title: Получение отзывов о товарах продавца
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/goods-feedback
operation_id: getGoodsFeedbacks
tags:
  - goods-feedback
  - fby
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 9a23d621e017c974
---

# Получение отзывов о товарах продавца

`POST /v2/businesses/{businessId}/goods-feedback`

{% include notitle [access](../../_auto/method_scopes/getGoodsFeedbacks.md) %} Возвращает отзывы о товарах продавца по указанным фильтрам. **Исключение:** отзывы, которые удалили покупатели или Маркет. {% note tip "Вы также можете настроить API-уведомления" %} Маркет отправит вам [запрос](../../push-notifications/reference/sendNotification.md), когда появится новый отзыв. А полную информацию о нем можно получить с помощью этого метода. [{#T}](../../push-notifications/index.md) {% endnote %} Результаты возвращаются постранично. Отзывы расположены в порядке публикации, поэтому вы можете передавать определенный идентификатор страницы в `pageToken`, если вы получали его ранее. {% include notitle [limit](../../_auto/method_limits/getGoodsFeedbacks.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |

## Запрос

**Тело запроса** (`application/json`):

- `feedbackIds` — array[integer<int64>]. Идентификаторы отзывов. ⚠️ Не используйте это поле одновременно с другими фильтрами. Если вы хотите воспользоваться ими, оставьте поле пустым.
- `dateTimeFrom` — string<date-time>. Начало периода. Не включительно. Если параметр не указан, возвращается информация за 6 месяцев до указанной в `dateTimeTo` даты. Максимальный интервал 6 месяцев.
- `dateTimeTo` — string<date-time>. Конец периода. Не включительно. Если параметр не указан, используется текущая дата. Максимальный интервал 6 месяцев.
- `reactionStatus` — string (ALL, NEED_REACTION). Нужно ли вернуть только непрочитанные отзывы. Для этого передайте значение `NEED_REACTION`. По умолчанию возвращаются все отзывы.
- `ratingValues` — array[integer<int32>]. Оценка товара.
- `offerIds` — array[string]. Фильтр по идентификатору товара.
- `paid` — boolean. Фильтр отзывов за баллы Плюса.

## Ответы

**200** — Список отзывов.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Список отзывов о товарах.
  - `feedbacks` — array[object] **обязательный**. Список отзывов.
    - `feedbackId` — integer<int64> **обязательный**. Идентификатор отзыва.
    - `createdAt` — string<date-time> **обязательный**. Дата и время создания отзыва.
    - `needReaction` — boolean **обязательный**. Прочитан ли отзыв. Принимает значение `false`, если магазин: * Прочитал отзыв в кабинете продавца на Маркете. * Отметил отзыв прочитанным — метод [POST v2/businesses/{businessId}/goods-feedback/skip-reaction](../../reference/goods-feedback/skipGoodsFeedbacksReaction.md). * Оставил комментарий к отзыву — метод [POST v2/businesses/{businessId}/goods-feedback/comments/update](../../reference/goods-feedback/updateGoodsFeedbackComment.md).
    - `identifiers` — object **обязательный**. Идентификаторы, которые связаны с отзывом.
      - `orderId` — integer<int64>. Идентификатор заказа на Маркете.
      - `offerId` — string. Идентификатор товара.
    - `author` — string. Имя автора отзыва.
    - `description` — object. Текстовая часть отзыва.
      - `advantages` — string. Описание плюсов товара в отзыве.
      - `disadvantages` — string. Описание минусов товара в отзыве.
      - `comment` — string. Комментарий в отзыве.
    - `media` — object. Фотографии и видео.
      - `photos` — array[string]. Ссылки на фотографии.
      - `videos` — array[string]. Ссылки на видео.
    - `statistics` — object **обязательный**. Статистическая информация по отзыву.
      - `rating` — integer<int32> **обязательный**. Оценка товара.
      - `commentsCount` — integer<int64> **обязательный**. Количество комментариев к отзыву. Учитываются только ответы на отзывы, а не дочерние комментарии.
      - `recommended` — boolean. Рекомендуют ли этот товар.
      - `paidAmount` — integer<int64>. Количество баллов Плюса, которое автор получил за отзыв.
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
