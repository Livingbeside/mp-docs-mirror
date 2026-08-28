---
title: Получение информации о заполненности карточек магазина
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/offer-cards
operation_id: getOfferCardsContentStatus
tags:
  - content
  - dbs
  - fby
  - fbs
  - express
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 4b4d067151411d8e
---

# Получение информации о заполненности карточек магазина

`POST /v2/businesses/{businessId}/offer-cards`

{% include notitle [access](../../_auto/method_scopes/getOfferCardsContentStatus.md) %} Возвращает сведения о состоянии контента для заданных товаров: * создана ли карточка товара и в каком она статусе; * рейтинг карточки — на сколько процентов она заполнена; * переданные характеристики товаров; * есть ли ошибки или предупреждения, связанные с контентом; * рекомендации по заполнению карточки. Чтобы получить другие характеристики товаров, воспользуйтесь методом [POST v2/businesses/{businessId}/offer-mappings](../../reference/business-offer-mappings/getOfferMappings.md). {% include notitle [limit](../../_auto/method_limits/getOfferCardsContentStatus.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |

## Запрос

**Тело запроса** (`application/json`):

- `offerIds` — array[string]. Идентификаторы товаров, информация о которых нужна. ⚠️ Не используйте это поле одновременно с фильтрами по статусам карточек, категориям, брендам или тегам. Если вы хотите воспользоваться фильтрами, оставьте поле пустым.
- `cardStatuses` — array[string (HAS_CARD_CAN_NOT_UPDATE, HAS_CARD_CAN_UPDATE, HAS_CARD_CAN_UPDATE_ERRORS, HAS_CARD_CAN_UPDATE_PROCESSING, NO_CARD_NEED_CONTENT, NO_CARD_MARKET_WILL_CREATE, NO_CARD_ERRORS, NO_CARD_PROCESSING, NO_CARD_ADD_TO_CAMPAIGN)]. Фильтр по статусам карточек. [Что такое карточка товара](https://yandex.ru/support/marketplace/assortment/content/index.html)
- `categoryIds` — array[integer<int32>]. Фильтр по категориям на Маркете.
- `withRecommendations` — boolean. Возвращать ли список рекомендаций к заполнению карточки и средний рейтинг карточки у товаров той категории, которая указана в `marketCategoryId`. Значение по умолчанию: `false`. Если информация нужна, передайте значение `true`. По умолчанию: `False`.

## Ответы

**200** — Информация о карточках указанных товаров.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Список товаров с информацией о состоянии карточек.
  - `offerCards` — array[object] **обязательный**. Страница списка товаров с информацией о состоянии карточек.
    - `offerId` — string **обязательный**. Ваш SKU — идентификатор товара в вашей системе. Правила использования SKU: * У каждого товара SKU должен быть свой. * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге. SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku). {% note warning %} Пробельные символы в начале и конце значения автоматически удаляются. Например, `" SKU123 "` и `"SKU123"` будут обработаны как одинаковые значения. {% endnote %} [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
    - `mapping` — object. Основная информация о карточке товара.
      - `marketSku` — integer<int64>. Идентификатор карточки на Маркете.
      - `marketSkuName` — string. Название карточки товара. Может отсутствовать в ответе, если товар еще не привязан к карточке.
      - `marketModelName` — string. {% note warning "Параметр устарел и будет отключен 12.10.2026." %} {% endnote %} Название модели на Маркете. Может отсутствовать в ответе, если товар еще не привязан к карточке.
      - `marketCategoryId` — integer<int64>. Идентификатор категории на Маркете, в которую попал товар. Может отсутствовать в ответе, если Маркет еще не определил категорию товара.
      - `marketCategoryName` — string. Название категории карточки на Маркете. Может отсутствовать в ответе, если Маркет еще не определил категорию товара.
    - `parameterValues` — array[object]. Список характеристик с их значениями.
      - `parameterId` — integer<int64> **обязательный**. Идентификатор характеристики.
      - `unitId` — integer<int64>. Идентификатор единицы измерения. Если вы не передали параметр `unitId`, используется единица измерения по умолчанию.
      - `valueId` — integer<int64>. Идентификатор значения. - Обязательно указывайте идентификатор, если передаете значение из перечня допустимых значений, полученного от Маркета. - Не указывайте для собственных значений. - Только для характеристик типа `ENUM`.
      - `value` — string. Значение. Для характеристик типа `ENUM` передавайте: - вместе с `valueId`, если значение берете из справочника; - без `valueId`, если значение собственное.
    - `cardStatus` — string (HAS_CARD_CAN_NOT_UPDATE, HAS_CARD_CAN_UPDATE, HAS_CARD_CAN_UPDATE_ERRORS, HAS_CARD_CAN_UPDATE_PROCESSING, NO_CARD_NEED_CONTENT, NO_CARD_MARKET_WILL_CREATE, NO_CARD_ERRORS, NO_CARD_PROCESSING, NO_CARD_ADD_TO_CAMPAIGN). Статус карточки.
    - `contentRating` — integer<int32>. Рейтинг карточки.
    - `averageContentRating` — integer<int32>. Средний рейтинг карточки у товаров той категории, которая указана в `marketCategoryId`. Возвращается, только если параметр `withRecommendations` имеет значение `true`.
    - `contentRatingStatus` — string (UPDATING, ACTUAL). Статус вычисления рейтинга карточки и рекомендаций.
    - `recommendations` — array[object]. Список рекомендаций к заполнению карточки. Возвращается, только если параметр `withRecommendations` имеет значение `true`. Рекомендации Маркета помогают заполнять карточку так, чтобы покупателям было проще найти ваш товар и решиться на покупку.
      - `type` — string (HAS_VIDEO, RECOGNIZED_VENDOR, MAIN, ADDITIONAL, DISTINCTIVE, FILTERABLE, PICTURE_COUNT, HAS_DESCRIPTION, HAS_BARCODE, FIRST_PICTURE_SIZE, TITLE_LENGTH, DESCRIPTION_LENGTH…) **обязательный**. Рекомендация.
      - `percent` — integer<int32>. Процент выполнения рекомендации. Указывается для рекомендаций некоторых типов: * `PICTURE_COUNT`. * `VIDEO_COUNT`. * `MAIN`. * `ADDITIONAL`. * `DISTINCTIVE`.
      - `remainingRatingPoints` — integer<int32>. Максимальное количество баллов рейтинга карточки, которые можно получить за выполнение рекомендаций.
    - `groupId` — string. Идентификатор группы товаров. У товаров, которые объединены в одну группу, будет одинаковый идентификатор. [Как объединить товары на карточке](../../step-by-step/assortment-add-goods.md#combine-variants)
    - `errors` — array[object]. Ошибки в контенте, препятствующие размещению товара на витрине.
      - `message` — string. Тип ошибки.
      - `comment` — string. Пояснение.
    - `warnings` — array[object]. Связанные с контентом предупреждения, не препятствующие размещению товара на витрине.
      - `message` — string. Тип ошибки.
      - `comment` — string. Пояснение.
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
