---
title: Информация о невыкупе или возврате
api: yandex-market
method: GET
path: /v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}
operation_id: getReturn
tags:
  - returns
  - fbs
  - dbs
  - express
  - fby
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 298fc60b23319d33
---

# Информация о невыкупе или возврате

`GET /v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}`

{% include notitle [access](../../_auto/method_scopes/getReturn.md) %} Получает информацию по одному невыкупу или возврату. {% note tip "Подключите API-уведомления" %} Маркет отправит вам запрос [POST notification](../../push-notifications/reference/sendNotification.md), когда появится новый невыкуп или возврат. [{#T}](../../push-notifications/index.md) {% endnote %} {% include notitle [limit](../../_auto/method_limits/getReturn.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `campaignId` | path | integer<int64> | да | Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия. Его можно узнать с помощью запроса [GET v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**: * блок **Идентификатор кампании**; * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**. ⚠️ Не путайте его с: - идентификатором магазина, который отображается в личном кабинете продавца; - рекламными кампаниями. |
| `orderId` | path | integer<int64> | да | Идентификатор заказа. |
| `returnId` | path | integer<int64> | да | Идентификатор невыкупа или возврата. |

## Ответы

**200** — Детали невыкупа или возврата.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Невыкуп или возврат в заказе. Параметров `logisticPickupPoint`, `shipmentRecipientType` и `shipmentStatus` может не быть в случае возврата: * С опцией **Быстрый возврат денег за дешевый брак**, когда товар остается у покупателя (`fastReturn=true`). * По заказу от бизнеса, если: * статус возврата `STARTED_BY_USER` или `WAITING_FOR_DECISION`; * возврат отменен до передачи товара. Статус возврата денег `refundStatus` актуален только для `returnType=RETURN`.
  - `id` — integer<int64> **обязательный**. Идентификатор невыкупа или возврата.
  - `orderId` — integer<int64> **обязательный**. Номер заказа.
  - `creationDate` — string<date-time>. Дата создания невыкупа или возврата. Формат даты: ISO 8601 со смещением относительно UTC.
  - `updateDate` — string<date-time>. Дата обновления невыкупа или возврата. Формат даты: ISO 8601 со смещением относительно UTC.
  - `refundStatus` — string (STARTED_BY_USER, REFUND_IN_PROGRESS, REFUNDED, FAILED, WAITING_FOR_DECISION, DECISION_MADE, REFUNDED_WITH_BONUSES, REFUNDED_BY_SHOP, CANCELLED, REJECTED, COMPLETE_WITHOUT_REFUND, PREMODERATION_DISPUTE…). Статус возврата денег: * `STARTED_BY_USER` — создан покупателем из личного кабинета. * `REFUND_IN_PROGRESS` — ждет решение о возврате денег (на рассмотрении). * `REFUNDED` — деньги возвращены. * `FAILED` — невозможно провести возврат покупателю. * `WAITING_FOR_DECISION` — ожидает решения (DBS). * `DECISION_MADE` — по возврату принято решение (DBS). * `REFUNDED_WITH_BONUSES` — возврат осуществлен баллами Плюса или промокодом. * `REFUNDED_BY_SHOP` — магазин сделал самостоятельно возврат денег. * `COMPLETE_WITHOUT_REFUND` — возврат денег не требуется. * `CANCELLED` — возврат отменен. * `REJECTED` — возврат отклонен модерацией или в ПВЗ. * `PREMODERATION_DISPUTE` — по возврату открыт спор (FBY, FBS и Экспресс). * `PREMODERATION_DECISION_WAITING` — ожидает решения (FBY, FBS и Экспресс). * `PREMODERATION_DECISION_MADE` — по возврату принято решение (FBY, FBS и Экспресс). * `PREMODERATION_SELECT_DELIVERY` — пользователь выбирает способ доставки (FBY, FBS и Экспресс). * `UNKNOWN` — неизвестный статус, обратитесь в поддержку.
  - `logisticPickupPoint` — object. Пункт вывоза.
    - `id` — integer<int64>. Идентификатор пункта вывоза.
    - `name` — string. Название пункта вывоза.
    - `address` — object. Адрес пункта вывоза.
      - `country` — string. Страна.
      - `city` — string. Город.
      - `street` — string. Улица.
      - `house` — string. Номер дома.
      - `postcode` — string. Почтовый индекс.
    - `instruction` — string. Дополнительные инструкции к вывозу.
    - `type` — string (WAREHOUSE, PICKUP_POINT, PICKUP_TERMINAL, PICKUP_POST_OFFICE, PICKUP_MIXED, PICKUP_RETAIL). Тип логистической точки.
    - `logisticPartnerId` — integer<int64>. Идентификатор логистического партнера, к которому относится логистическая точка.
  - `pickupTillDate` — string<date-time>. Дата, до которой можно забрать товар. Только для невыкупов и возвратов в логистическом статусе `READY_FOR_PICKUP`. Формат даты: ISO 8601 со смещением относительно UTC.
  - `shipmentRecipientType` — string (SHOP, DELIVERY_SERVICE, POST). Способ возврата товара покупателем.
  - `shipmentStatus` — string (CREATED, RECEIVED, IN_TRANSIT, READY_FOR_PICKUP, PICKED, LOST, EXPIRED, CANCELLED, FULFILMENT_RECEIVED, PREPARED_FOR_UTILIZATION, NOT_IN_DEMAND, UTILIZED…). Статус передачи возврата.
  - `refundAmount` — integer<int64>. {% note warning "Параметр устарел и будет отключен 12.10.2026." %} Вместо него используйте `amount`. {% endnote %} Сумма возврата в копейках.
  - `amount` — object. Сумма возврата.
    - `value` — number **обязательный**. Значение.
    - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
  - `items` — array[object] **обязательный**. Список товаров в невыкупе или возврате.
    - `marketSku` — integer<int64>. Идентификатор карточки товара на Маркете.
    - `shopSku` — string **обязательный**. Ваш SKU — идентификатор товара в вашей системе. Правила использования SKU: * У каждого товара SKU должен быть свой. * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге. SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku). {% note warning %} Пробельные символы в начале и конце значения автоматически удаляются. Например, `" SKU123 "` и `"SKU123"` будут обработаны как одинаковые значения. {% endnote %} [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
    - `count` — integer<int64> **обязательный**. Количество единиц товара.
    - `decisions` — array[object]. Список решений по возврату.
      - `returnItemId` — integer<int64>. Идентификатор товара в возврате.
      - `count` — integer<int32>. Количество единиц товара.
      - `comment` — string. Комментарий.
      - `reasonType` — string (BAD_QUALITY, DOES_NOT_FIT, WRONG_ITEM, DAMAGE_DELIVERY, LOYALTY_FAIL, CONTENT_FAIL, DELIVERY_FAIL, UNKNOWN). Причины возврата: * `BAD_QUALITY` — бракованный товар (есть недостатки). * `DOES_NOT_FIT` — товар не подошел. * `WRONG_ITEM` — привезли не тот товар. * `DAMAGE_DELIVERY` — товар поврежден при доставке. * `LOYALTY_FAIL` — невозможно установить виновного в браке/пересорте. * `CONTENT_FAIL` — ошибочное описание товара по вине Маркета. * `DELIVERY_FAIL` — товар не привезли. * `UNKNOWN` — причина не известна.
      - `subreasonType` — string (USER_DID_NOT_LIKE, USER_CHANGED_MIND, DELIVERED_TOO_LONG, BAD_PACKAGE, DAMAGED, NOT_WORKING, INCOMPLETENESS, WRONG_ITEM, WRONG_COLOR, DID_NOT_MATCH_DESCRIPTION, WRONG_ORDER, WRONG_AMOUNT_DELIVERED…). Детали причин возврата: * `DOES_NOT_FIT`: * `USER_DID_NOT_LIKE` — товар не понравился. * `USER_CHANGED_MIND` — передумал покупать. * `DELIVERED_TOO_LONG` — передумал покупать из-за длительного срока доставки. * `BAD_QUALITY`: * `BAD_PACKAGE` — заводская упаковка повреждена. * `DAMAGED` — царапины, сколы. * `NOT_WORKING` — не включается, не работает. * `INCOMPLETENESS` — некомплект (не хватает детали в наборе, к товару). * `WRAPPING_DAMAGED` — транспортная упаковка повреждена. * `ITEM_WAS_USED` — следы использования на товаре. * `BROKEN` — товар разбит. * `BAD_FLOWERS` — некачественные цветы. * `WRONG_ITEM`: * `WRONG_ITEM` — не тот товар. * `WRONG_COLOR` — цвет не соответствует заявленному. * `DID_NOT_MATCH_DESCRIPTION` — описание или характеристики не соответствуют заявленным. * `WRONG_ORDER` — доставили чужой заказ. * `WRONG_AMOUNT_DELIVERED` — неверное количество товара. * `PARCEL_MISSING` — часть заказа отсутствует. * `INCOMPLETE` — заказ не привезли полностью. * `UNKNOWN` — детали причины не указаны.
      - `decisionType` — string (FAST_REFUND_MONEY, REFUND_MONEY, REFUND_MONEY_INCLUDING_SHIPMENT, REPAIR, REPLACE, SEND_TO_EXAMINATION, DECLINE_REFUND, PARTIAL_MONEY_REFUND, OTHER_DECISION, UNKNOWN). Решение по возврату: * `FAST_REFUND_MONEY` — вернуть покупателю деньги без возврата товара. * `REFUND_MONEY` — вернуть покупателю деньги за товар. * `REFUND_MONEY_INCLUDING_SHIPMENT` — вернуть покупателю деньги за товар и обратную пересылку. * `REPAIR` — отремонтировать товар. * `REPLACE` — заменить товар. * `SEND_TO_EXAMINATION` — взять товар на экспертизу. * `DECLINE_REFUND` — отказать в возврате. * `PARTIAL_MONEY_REFUND` — частичный возврат денег. * `OTHER_DECISION` — другое решение. * `UNKNOWN` — не указано.
      - `refundAmount` — integer<int64>. {% note warning "Параметр устарел и будет отключен 12.10.2026." %} Вместо него используйте `amount`. {% endnote %} Сумма возврата в копейках.
      - `amount` — object. Сумма возврата.
        - `value` — number **обязательный**. Значение.
        - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
      - `partnerCompensation` — integer<int64>. {% note warning "Параметр устарел и будет отключен 12.10.2026." %} Вместо него используйте `partnerCompensationAmount`. {% endnote %} Компенсация за обратную доставку в копейках.
      - `partnerCompensationAmount` — object. Компенсация за обратную доставку.
        - `value` — number **обязательный**. Значение.
        - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
      - `images` — array[string]. Список хеш-кодов фотографий товара от покупателя.
    - `instances` — array[object]. Список логистических позиций возврата.
      - `stockType` — string (FIT, DEFECT, ANOMALY, SURPLUS, EXPIRED, MISGRADING, UNDEFINED, INCORRECT_IMEI, INCORRECT_SERIAL_NUMBER, INCORRECT_CIS, PART_MISSING, NON_COMPLIENT…). Тип остатка на складе.
      - `status` — string (CREATED, RECEIVED, IN_TRANSIT, READY_FOR_PICKUP, PICKED, RECEIVED_ON_FULFILLMENT, CANCELLED, LOST, UTILIZED, PREPARED_FOR_UTILIZATION, EXPROPRIATED, NOT_IN_DEMAND). Логистический статус конкретного товара.
      - `cis` — string. Код идентификации единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов :no-translate[Market Yandex Go]).
      - `imei` — string. Международный идентификатор мобильного оборудования.
    - `tracks` — array[object]. Список трек-кодов для почтовых отправлений.
      - `trackCode` — string. Трек-код почтового отправления.
  - `returnType` — string (UNREDEEMED, RETURN) **обязательный**. Тип возврата.
  - `fastReturn` — boolean. Используется ли опция **Быстрый возврат денег за дешевый брак**. Актуально только для `returnType=RETURN`.

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
