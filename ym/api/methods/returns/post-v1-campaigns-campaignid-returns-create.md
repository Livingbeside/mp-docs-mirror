---
title: Создание возврата
api: yandex-market
method: POST
path: /v1/campaigns/{campaignId}/returns/create
operation_id: createReturn
tags:
  - returns
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: b802ad82f9bc2996
---

# Создание возврата

`POST /v1/campaigns/{campaignId}/returns/create`

{% include notitle [access](../../_auto/method_scopes/createReturn.md) %}

Создает новый возврат.

Это можно сделать только для заказа в статусе `DELIVERED`.

{% note warning "Перед вызовом метода" %}

Проверьте, подходят ли пункты выдачи для возврата указанных товаров, — [POST v1/campaigns/{campaignId}/return-delivery-options](../../reference/delivery-options/getReturnDeliveryOptions.md).

{% endnote %}

{% include notitle [limit](../../_auto/method_limits/createReturn.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `campaignId` | path | integer<int64> | да | Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия. Его можно узнать с помощью запроса [GET v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**: * блок **Идентификатор кампании**; * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**. ⚠️ Не путайте его с: - идентификатором магазина, который отображается в личном кабинете продавца; - рекламными кампаниями. |

## Запрос

**Тело запроса** (`application/json`):

- `newReturn` — object **обязательный**. Информация о возврате.
  - `externalReturnId` — string **обязательный**. Внешний идентификатор возврата в системе магазина.
  - `orderId` — integer<int64> **обязательный**. Идентификатор заказа, по которому нужно сделать возврат.
  - `items` — array[object] **обязательный**. Список товаров в возврате.
    - `offerId` — string **обязательный**. Ваш SKU — идентификатор товара в вашей системе. Правила использования SKU: * У каждого товара SKU должен быть свой. * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге. SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku). {% note warning %} Пробельные символы в начале и конце значения автоматически удаляются. Например, `" SKU123 "` и `"SKU123"` будут обработаны как одинаковые значения. {% endnote %} [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
    - `count` — integer<int32> **обязательный**. Количество единиц товара.
    - `reasonType` — string (BAD_QUALITY, DOES_NOT_FIT, WRONG_ITEM) **обязательный**. Причины возврата: * `BAD_QUALITY` — бракованный товар (есть недостатки). * `DOES_NOT_FIT` — товар не подошел. * `WRONG_ITEM` — привезли не тот товар.
    - `subreasonType` — string (USER_DID_NOT_LIKE, USER_CHANGED_MIND, DELIVERED_TOO_LONG, BAD_PACKAGE, DAMAGED, NOT_WORKING, INCOMPLETENESS, WRONG_ITEM, WRONG_COLOR, DID_NOT_MATCH_DESCRIPTION) **обязательный**. Детали причин возврата: * `DOES_NOT_FIT`: * `USER_DID_NOT_LIKE` — товар не понравился. * `USER_CHANGED_MIND` — передумал покупать. * `DELIVERED_TOO_LONG` — передумал покупать из-за длительного срока доставки. * `BAD_QUALITY`: * `BAD_PACKAGE` — заводская упаковка повреждена. * `DAMAGED` — царапины, сколы. * `NOT_WORKING` — не включается, не работает. * `INCOMPLETENESS` — некомплект (не хватает детали в наборе, к товару). * `WRONG_ITEM`: * `WRONG_ITEM` — не тот товар. * `WRONG_COLOR` — цвет не соответствует заявленному. * `DID_NOT_MATCH_DESCRIPTION` — описание или характеристики не соответствуют заявленным.
    - `comment` — string. Комментарий к товару в возврате.
    - `pictures` — array[string]. Ссылки (URL) на изображения товара в возврате.
  - `customer` — object **обязательный**. Данные получателя заказа или отправителя возврата.
    - `firstName` — string **обязательный**. Имя.
    - `lastName` — string **обязательный**. Фамилия.
    - `middleName` — string. Отчество.
    - `phone` — string **обязательный**. Номер телефона. Формат: `+ `.
  - `returnOption` — object **обязательный**. Информация о способе возврата.
    - `pickupReturn` — object **обязательный**. Информация о пункте выдачи, в который нужно вернуть товары. [Как получить список подходящих пунктов выдачи](../../reference/delivery-options/getReturnDeliveryOptions.md)
      - `logisticPointId` — integer<int64> **обязательный**. Идентификатор пункта выдачи. Его можно узнать с помощью метода [POST v1/businesses/{businessId}/logistics-points](../../reference/logistic-points/getLogisticPoints.md).

## Ответы

**200** — Информация о cозданном возврате.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация о созданном возврате.
  - `id` — integer<int64> **обязательный**. Идентификатор возврата.

**400** — Запрос содержит неправильные данные. [Подробнее об ошибках при работе с заказами](../../concepts/error-codes#orders)

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

**500** — Внутренняя ошибка Маркета. [Подробнее об ошибке](../../concepts/error-codes.md#500)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.
