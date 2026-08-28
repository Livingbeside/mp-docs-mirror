---
title: Генерация штрихкодов
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/offer-mappings/barcodes/generate
operation_id: generateOfferBarcodes
tags:
  - business-offer-mappings
  - dbs
  - fby
  - fbs
  - express
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 313c0845b4685965
---

# Генерация штрихкодов

`POST /v1/businesses/{businessId}/offer-mappings/barcodes/generate`

{% include notitle [access](../../_auto/method_scopes/generateOfferBarcodes.md) %} Генерирует штрихкоды и присваивает их указанным товарам. Если у товара на упаковке уже есть штрихкод производителя, передайте его в параметре `barcodes` в методе [POST v2/businesses/{businessId}/offer-mappings/update](../../reference/business-offer-mappings/updateOfferMappings.md). Генерировать новый не нужно. {% include notitle [limit](../../_auto/method_limits/generateOfferBarcodes.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `offerIds` — array[string] **обязательный**. Список товаров, для которых нужно сгенерировать штрихкоды.
- `skipIfExists` — boolean. Для каких товаров нужно сгенерировать штрихкоды: * `false` — для всех, которые переданы в запросе. * `true` — только для тех, у которых их нет. По умолчанию: `True`.

## Ответы

**200** — Пустой ответ, если генерация успешно завершилась для всех переданных товаров. Или список товаров, для которых не удалось сгенерировать штрихкоды.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Товары, для которых не удалось сгенерировать штрихкоды. Проверьте корректность переданных `offerId`. Если ошибка повторяется, обратитесь в службу поддержки — перейдите в [кабинет продавца на Маркете](https://partner.market.yandex.ru/business/any/support) и нажмите кнопку **Создать обращение**.
  - `unprocessedOfferIds` — array[string] **обязательный**. Список товаров, для которых не удалось сгенерировать штрихкоды.

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

**420** — Превышено ограничение на доступ к ресурсу. [Подробнее об ошибке](../../concepts/error-codes.md#420)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**423** — К ресурсу нельзя применить указанный метод. [Подробнее об ошибке](../../concepts/error-codes.md#423)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**500** — Внутренняя ошибка Маркета. [Подробнее об ошибке](../../concepts/error-codes.md#500)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.
