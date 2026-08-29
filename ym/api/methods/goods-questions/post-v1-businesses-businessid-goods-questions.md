---
title: Получение вопросов о товарах продавца
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/goods-questions
operation_id: getGoodsQuestions
tags:
  - goods-questions
  - fby
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: eeaf50ecbcef1fda
---

# Получение вопросов о товарах продавца

`POST /v1/businesses/{businessId}/goods-questions`

{% include notitle [access](../../_auto/method_scopes/getGoodsQuestions.md) %}

Возвращает вопросы о товарах продавца по указанным фильтрам.

{% note tip "Вы также можете настроить API-уведомления" %}

Маркет отправит вам [запрос](../../push-notifications/reference/sendNotification.md), когда появится новый вопрос. А полную информацию о нем можно получить с помощью этого метода.

[{#T}](../../push-notifications/index.md)

{% endnote %}

Результаты возвращаются постранично, одна страница содержит не более 50 вопросов.

{% include notitle [limit](../../_auto/method_limits/getGoodsQuestions.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | — |

## Запрос

**Тело запроса** (`application/json`):

- `categoryIds` — array[integer<int64>]. Идентификаторы категорий товаров.
- `questionIds` — array[integer<int64>]. Идентификаторы вопросов.
- `dateFrom` — string<date>. Дата начала периода создания вопроса. Если параметр не указан, возвращается информация за 1 месяц до указанной в `dateTo` даты. Максимальный интервал 1 месяц.
- `dateTo` — string<date>. Дата окончания периода создания вопроса. Если параметр не указан, используется текущая дата. Максимальный интервал 1 месяц.
- `needAnswer` — boolean. Нужен ли ответ на вопрос. * `true` — только вопросы, которые ждут ответа. * `false` — все вопросы. По умолчанию: `False`.
- `sort` — string (CREATED_AT_DESC, CREATED_AT_ASC). Порядок сортировки вопросов. * `CREATED_AT_DESC` — по дате создания вопроса по убыванию; * `CREATED_AT_ASC` — по дате создания вопроса по возрастанию.

## Ответы

**200** — Список вопросов.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Список вопросов.
  - `questions` — array[object] **обязательный**. Список вопросов.
    - `questionIdentifiers` — object **обязательный**. Идентификаторы вопроса.
      - `id` — integer<int64> **обязательный**. Идентификатор вопроса.
      - `categoryId` — integer<int64>. Идентификатор категории.
      - `offerId` — string **обязательный**. Ваш SKU — идентификатор товара в вашей системе. Правила использования SKU: * У каждого товара SKU должен быть свой. * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге. SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku). {% note warning %} Пробельные символы в начале и конце значения автоматически удаляются. Например, `" SKU123 "` и `"SKU123"` будут обработаны как одинаковые значения. {% endnote %} [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
    - `businessId` — integer<int64> **обязательный**. Идентификатор кабинета. {% if audience == "partner" %}Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %}
    - `text` — string **обязательный**. Текстовое содержимое.
    - `createdAt` — string<date-time> **обязательный**. Дата и время создания вопроса.
    - `votes` — object **обязательный**. Количество лайков и дизлайков на вопросе, ответе или комментарии.
      - `likes` — integer<int64> **обязательный**. Количество лайков.
      - `dislikes` — integer<int64> **обязательный**. Количество дизлайков.
    - `author` — object **обязательный**. Информация об авторе комментария.
      - `type` — string (USER, BUSINESS, VENDOR, BRAND). Тип автора: * `USER` — пользователь. * `BUSINESS` — кабинет. * `VENDOR` — производитель. * `BRAND` — бренд.
      - `name` — string. Имя автора или название кабинета.
  - `paging` — object. Идентификатор следующей страницы.
    - `nextPageToken` — string. Идентификатор следующей страницы результатов.
  - `totalCount` — integer<int64> **обязательный**. Общее количество вопросов, которые попадают под фильтр.

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
