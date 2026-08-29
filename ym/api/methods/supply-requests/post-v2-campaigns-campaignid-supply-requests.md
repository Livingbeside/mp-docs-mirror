---
title: Получение информации о заявках на поставку, вывоз и утилизацию
api: yandex-market
method: POST
path: /v2/campaigns/{campaignId}/supply-requests
operation_id: getSupplyRequests
tags:
  - supply-requests
  - fby
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 7709f7ecb3f8872a
---

# Получение информации о заявках на поставку, вывоз и утилизацию

`POST /v2/campaigns/{campaignId}/supply-requests`

{% include notitle [access](../../_auto/method_scopes/getSupplyRequests.md) %}

По указанным фильтрам возвращает заявки на поставку, вывоз и утилизацию, а также информацию по ним.

{% include notitle [limit](../../_auto/method_limits/getSupplyRequests.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `campaignId` | path | integer<int64> | да | Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия. Его можно узнать с помощью запроса [GET v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**: * блок **Идентификатор кампании**; * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**. ⚠️ Не путайте его с: - идентификатором магазина, который отображается в личном кабинете продавца; - рекламными кампаниями. |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | — |

## Запрос

**Тело запроса** (`application/json`):

- `requestIds` — array[integer<int64>]. Идентификаторы заявок.
- `requestDateFrom` — string<date-time>. Дата начала периода для фильтрации заявок.
- `requestDateTo` — string<date-time>. Дата окончания периода для фильтрации заявок.
- `requestTypes` — array[string (SUPPLY, WITHDRAW, UTILIZATION)]. Типы заявок для фильтрации.
- `requestSubtypes` — array[string (DEFAULT, XDOC, INVENTORYING_SUPPLY, INVENTORYING_SUPPLY_WAREHOUSE_BASED_PER_SUPPLIER, MOVEMENT_SUPPLY, ADDITIONAL_SUPPLY, VIRTUAL_DISTRIBUTION_CENTER, VIRTUAL_DISTRIBUTION_CENTER_CHILD, FORCE_PLAN, FORCE_PLAN_ANOMALY_PER_SUPPLY, PLAN_BY_SUPPLIER, ANOMALY_WITHDRAW…)]. Подтипы заявок для фильтрации.
- `requestStatuses` — array[string (CREATED, FINISHED, CANCELLED, INVALID, VALIDATED, PUBLISHED, ARRIVED_TO_SERVICE, ARRIVED_TO_XDOC_SERVICE, SHIPPED_TO_SERVICE, CANCELLATION_REQUESTED, CANCELLATION_REJECTED, REGISTERED_IN_ELECTRONIC_QUEUE…)]. Статусы заявок для фильтрации.
- `sorting` — object. Параметры сортировки.
  - `direction` — string (ASC, DESC) **обязательный**. Направление сортировки: - `ASC` — сортировка по возрастанию. - `DESC` — сортировка по убыванию.
  - `attribute` — string (ID, REQUESTED_DATE, UPDATED_AT, STATUS) **обязательный**. По какому параметру сортировать заявки: * `ID` — идентификатор заявки. * `REQUESTED_DATE` — дата поставки на склад хранения. Если товары проходили через транзитный склад, сортирует по датам поставки на оба склада. * `UPDATED_AT` — время обновления заявки. * `STATUS` — статус заявки.

## Ответы

**200** — Список заявок и информация по ним.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Список заявок и информация по ним.
  - `requests` — array[object] **обязательный**. Список заявок.
    - `id` — object **обязательный**. Идентификатор и номера заявки.
      - `id` — integer<int64> **обязательный**. Идентификатор заявки. {% note warning "Используется только в API" %} По нему не получится найти заявки в кабинете продавца на Маркете. Для этого используйте `marketplaceRequestId` или `warehouseRequestId`. {% endnote %}
      - `marketplaceRequestId` — string. Номер заявки на маркетплейсе. Также указывается в кабинете продавца на Маркете.
      - `warehouseRequestId` — string. Номер заявки на складе. Также указывается в кабинете продавца на Маркете.
    - `type` — string (SUPPLY, WITHDRAW, UTILIZATION) **обязательный**. Тип заявки.
    - `subtype` — string (DEFAULT, XDOC, INVENTORYING_SUPPLY, INVENTORYING_SUPPLY_WAREHOUSE_BASED_PER_SUPPLIER, MOVEMENT_SUPPLY, ADDITIONAL_SUPPLY, VIRTUAL_DISTRIBUTION_CENTER, VIRTUAL_DISTRIBUTION_CENTER_CHILD, FORCE_PLAN, FORCE_PLAN_ANOMALY_PER_SUPPLY, PLAN_BY_SUPPLIER, ANOMALY_WITHDRAW…) **обязательный**. Подтип заявки.
    - `status` — string (CREATED, FINISHED, CANCELLED, INVALID, VALIDATED, PUBLISHED, ARRIVED_TO_SERVICE, ARRIVED_TO_XDOC_SERVICE, SHIPPED_TO_SERVICE, CANCELLATION_REQUESTED, CANCELLATION_REJECTED, REGISTERED_IN_ELECTRONIC_QUEUE…) **обязательный**. Статус заявки.
    - `updatedAt` — string<date-time> **обязательный**. Дата и время последнего обновления заявки.
    - `counters` — object **обязательный**. Количество товаров, коробок и палет в заявке.
      - `planCount` — integer<int32>. Количество товаров в заявке на поставку.
      - `factCount` — integer<int32>. Количество товаров, которые приняты на складе.
      - `undefinedCount` — integer<int32>. Количество непринятых товаров.
      - `surplusCount` — integer<int32>. Количество лишних товаров.
      - `shortageCount` — integer<int32>. Количество товаров с недостатками.
      - `defectCount` — integer<int32>. Количество товаров с браком.
      - `acceptableCount` — integer<int32>. Количество товаров, которые можно привезти дополнительно.
      - `unacceptableCount` — integer<int32>. Количество товаров, которые нельзя привезти дополнительно.
      - `actualPalletsCount` — integer<int32>. Количество палет, которые приняты на складе.
      - `actualBoxCount` — integer<int32>. Количество коробок, которые приняты на складе.
    - `parentLink` — object. Ссылка на родительскую заявку.
      - `id` — object **обязательный**. Идентификаторы связанной заявки.
        - `id` — integer<int64> **обязательный**. Идентификатор заявки. {% note warning "Используется только в API" %} По нему не получится найти заявки в кабинете продавца на Маркете. Для этого используйте `marketplaceRequestId` или `warehouseRequestId`. {% endnote %}
        - `marketplaceRequestId` — string. Номер заявки на маркетплейсе. Также указывается в кабинете продавца на Маркете.
        - `warehouseRequestId` — string. Номер заявки на складе. Также указывается в кабинете продавца на Маркете.
      - `type` — string (VIRTUAL_DISTRIBUTION, WITHDRAW, UTILIZATION, ADDITIONAL_SUPPLY) **обязательный**. Тип связи.
    - `childrenLinks` — array[object]. Ссылки на дочерние заявки.
      - `id` — object **обязательный**. Идентификаторы связанной заявки.
        - `id` — integer<int64> **обязательный**. Идентификатор заявки. {% note warning "Используется только в API" %} По нему не получится найти заявки в кабинете продавца на Маркете. Для этого используйте `marketplaceRequestId` или `warehouseRequestId`. {% endnote %}
        - `marketplaceRequestId` — string. Номер заявки на маркетплейсе. Также указывается в кабинете продавца на Маркете.
        - `warehouseRequestId` — string. Номер заявки на складе. Также указывается в кабинете продавца на Маркете.
      - `type` — string (VIRTUAL_DISTRIBUTION, WITHDRAW, UTILIZATION, ADDITIONAL_SUPPLY) **обязательный**. Тип связи.
    - `targetLocation` — object **обязательный**. Информация о складе хранения или ПВЗ.
      - `requestedDate` — string<date-time>. Дата и время поставки на склад или в ПВЗ.
      - `serviceId` — integer<int64> **обязательный**. Идентификатор склада или логистического партнера ПВЗ.
      - `name` — string **обязательный**. Название склада или ПВЗ.
      - `address` — object **обязательный**. Адрес склада или ПВЗ.
        - `fullAddress` — string **обязательный**. Полный адрес склада или ПВЗ.
        - `gps` — object **обязательный**. GPS-координаты широты и долготы.
          - `latitude` — number **обязательный**. Широта.
          - `longitude` — number **обязательный**. Долгота.
      - `type` — string (FULFILLMENT, XDOC, PICKUP_POINT) **обязательный**. Тип склада или ПВЗ: * `FULFILLMENT` — склад хранения. * `XDOC` — транзитный склад. * `PICKUP_POINT` — ПВЗ.
    - `transitLocation` — object. Информация о транзитном складе или ПВЗ.
      - `requestedDate` — string<date-time>. Дата и время поставки на склад или в ПВЗ.
      - `serviceId` — integer<int64> **обязательный**. Идентификатор склада или логистического партнера ПВЗ.
      - `name` — string **обязательный**. Название склада или ПВЗ.
      - `address` — object **обязательный**. Адрес склада или ПВЗ.
        - `fullAddress` — string **обязательный**. Полный адрес склада или ПВЗ.
        - `gps` — object **обязательный**. GPS-координаты широты и долготы.
          - `latitude` — number **обязательный**. Широта.
          - `longitude` — number **обязательный**. Долгота.
      - `type` — string (FULFILLMENT, XDOC, PICKUP_POINT) **обязательный**. Тип склада или ПВЗ: * `FULFILLMENT` — склад хранения. * `XDOC` — транзитный склад. * `PICKUP_POINT` — ПВЗ.
  - `paging` — object. Информация о страницах с результатами.
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
