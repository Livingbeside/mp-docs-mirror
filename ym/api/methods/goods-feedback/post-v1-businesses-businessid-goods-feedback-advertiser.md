---
title: Получение отзывов о товарах для рекламодателей
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/goods-feedback-advertiser
operation_id: getGoodsFeedbacksUrbanads
tags:
  - goods-feedback
  - fby
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 28e0718158c988fd
---

# Получение отзывов о товарах для рекламодателей

`POST /v1/businesses/{businessId}/goods-feedback-advertiser`

{% include notitle [access](../../_auto/method_scopes/getGoodsFeedbacksUrbanads.md) %} Возвращает отзывы о товарах бренда по указанным фильтрам. **Исключение:** отзывы, которые удалили покупатели или Маркет. Результаты возвращаются постранично. Отзывы расположены в порядке публикации, поэтому вы можете передавать определенный идентификатор страницы в `pageToken`, если вы получали его ранее. {% include notitle [limit](../../_auto/method_limits/getGoodsFeedbacksUrbanads.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |
| `sourceType` | query | string (SELLER, ADVERTISER) | нет | Признак типа кабинета, от имени которого вызывается метод: {% if audience == "partner" %} - `SELLER` — продавец. {% endif %} - `ADVERTISER` — рекламодатель. {% if audience == "advertiser" %} {% note info "Обязательно указывайте sourceType=ADVERTISER в каждом запросе." %} {% endnote %} {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `feedbackIds` — array[integer<int64>]. Идентификаторы отзывов. ⚠️ Не используйте это поле одновременно с другими фильтрами. Если вы хотите воспользоваться ими, оставьте поле пустым.
- `dateTimeFrom` — string<date-time>. Начало периода. Не включительно. Если параметр не указан, возвращается информация за 6 месяцев до указанной в `dateTimeTo` даты. Максимальный интервал 6 месяцев.
- `dateTimeTo` — string<date-time>. Конец периода. Не включительно. Если параметр не указан, используется текущая дата. Максимальный интервал 6 месяцев.
- `reactionStatus` — string (ALL, NEED_REACTION). Нужно ли вернуть только непрочитанные отзывы. Для этого передайте значение `NEED_REACTION`. По умолчанию возвращаются все отзывы.
- `ratingValues` — array[integer<int32>]. Оценка товара.
- `paid` — boolean. Фильтр отзывов за баллы Плюса.

## Ответы

**200** — Список отзывов.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Список отзывов о товарах.
  - `feedbacks` — array[object] **обязательный**. Список отзывов.
    - `feedbackId` — integer<int64> **обязательный**. Идентификатор отзыва.
    - `createdAt` — string<date-time> **обязательный**. Дата и время создания отзыва.
    - `needReaction` — boolean **обязательный**. Прочитан ли отзыв. Принимает значение `false`, если рекламодатель: * Прочитал отзыв в кабинете UrbanAds. * Пропустил реакцию на отзыв — метод [POST v2/businesses/{businessId}/goods-feedback/skip-reaction](../../reference/goods-feedback/skipGoodsFeedbacksReaction.md). * Оставил комментарий к отзыву — метод [POST v2/businesses/{businessId}/goods-feedback/comments/update](../../reference/goods-feedback/updateGoodsFeedbackComment.md).
    - `context` — object **обязательный**. Информация о товаре, бизнесе и бренде, которые связаны с отзывом.
      - `offerName` — string. Название товара, под которым оставлен отзыв.
      - `pictureUrl` — string. Ссылка на фотографию товара.
      - `businessId` — integer<int64>. Идентификатор бизнеса, под товаром которого оставлен отзыв.
      - `businessName` — string. Название бизнеса, под товаром которого оставлен отзыв.
      - `brandId` — string. Идентификатор бренда товара.
      - `brandName` — string. Название бренда товара.
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
