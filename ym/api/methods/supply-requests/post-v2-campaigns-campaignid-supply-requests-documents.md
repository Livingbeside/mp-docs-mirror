---
title: Получение документов по заявке на поставку, вывоз или утилизацию
api: yandex-market
method: POST
path: /v2/campaigns/{campaignId}/supply-requests/documents
operation_id: getSupplyRequestDocuments
tags:
  - supply-requests
  - fby
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 97a810229c953fae
---

# Получение документов по заявке на поставку, вывоз или утилизацию

`POST /v2/campaigns/{campaignId}/supply-requests/documents`

{% include notitle [access](../../_auto/method_scopes/getSupplyRequestDocuments.md) %} Возвращает документы по заявке. {% include notitle [limit](../../_auto/method_limits/getSupplyRequestDocuments.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `campaignId` | path | integer<int64> | да | Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия. Его можно узнать с помощью запроса [GET v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**: * блок **Идентификатор кампании**; * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**. ⚠️ Не путайте его с: - идентификатором магазина, который отображается в личном кабинете продавца; - рекламными кампаниями. |

## Запрос

**Тело запроса** (`application/json`):

- `requestId` — integer<int64> **обязательный**. Идентификатор заявки. {% note warning "Используется только в API" %} По нему не получится найти заявки в кабинете продавца на Маркете. Для этого используйте `marketplaceRequestId` или `warehouseRequestId`. {% endnote %}

## Ответы

**200** — Список документов и ссылки на них.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация о документах по заявке.
  - `documents` — array[object] **обязательный**. Список документов.
    - `type` — string (SUPPLY, ADDITIONAL_SUPPLY, VIRTUAL_DISTRIBUTION_CENTER_SUPPLY, TRANSFER, INBOUND_UTD, OUTBOUND_UTD, ADDITIONAL_SUPPLY_ACCEPTABLE_GOODS, ADDITIONAL_SUPPLY_UNACCEPTABLE_GOODS, VALIDATION_ERRORS, WITHDRAW, ACT_OF_WITHDRAW, ANOMALY_CONTAINERS_WITHDRAW_ACT…) **обязательный**. Тип документа: * **Документы, которые загружает магазин** * `SUPPLY` — список товаров. * `ADDITIONAL_SUPPLY` — список товаров в дополнительной поставке. * `VIRTUAL_DISTRIBUTION_CENTER_SUPPLY` — список товаров в [мультипоставке](*multisupply). * `TRANSFER` — список товаров для утилизации. * `WITHDRAW` — список товаров для вывоза. * **Поставка товаров** * `VALIDATION_ERRORS` — ошибки по товарам в поставке. * `CARGO_UNITS` — ярлыки для грузомест. * **Дополнительная поставка и непринятые товары** * `ADDITIONAL_SUPPLY_ACCEPTABLE_GOODS` — товары, которые подходят для дополнительной поставки. * `ADDITIONAL_SUPPLY_UNACCEPTABLE_GOODS` — вывоз непринятых товаров. * **Маркировка товаров** * `INBOUND_UTD` — входящий УПД. * `OUTBOUND_UTD` — исходящий УПД. * `IDENTIFIERS` — коды маркировки товаров. * `CIS_FACT` — принятые товары с кодами маркировки. * `ITEMS_WITH_CISES` — товары, для которых нужна маркировка. * `REPORT_OF_WITHDRAW_WITH_CISES` — маркированные товары для вывоза со склада. * `SECONDARY_ACCEPTANCE_CISES` — маркированные товары, которые приняты после вторичной приемки. * `RNPT_FACT` — принятые товары с регистрационным номером партии товара (РНПТ). * **Акты** * `ACT_OF_WITHDRAW` — акт возврата. * `ANOMALY_CONTAINERS_WITHDRAW_ACT` — акт изъятия непринятого товара. * `ACT_OF_WITHDRAW_FROM_STORAGE` — акт списания с ответственного хранения. * `ACT_OF_RECEPTION_TRANSFER` — акт приема-передачи. * `ACT_OF_DISCREPANCY` — акт о расхождениях. * `SECONDARY_RECEPTION_ACT` — акт вторичной приемки.
    - `url` — string **обязательный**. Ссылка на документ.
    - `createdAt` — string<date-time> **обязательный**. Дата и время создания документа.

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
