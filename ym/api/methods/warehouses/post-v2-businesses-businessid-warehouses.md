---
title: Список складов
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/warehouses
operation_id: getPagedWarehouses
tags:
  - warehouses
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 0fb42f45d6341118
---

# Список складов

`POST /v2/businesses/{businessId}/warehouses`

{% include notitle [access](../../_auto/method_scopes/getPagedWarehouses.md) %} Возвращает список складов и информацию о них. {% note warning "Когда использовать этот метод" %} Метод актуален для кабинетов с группами складов. Если в кабинете нет групп складов, используйте метод [POST v3/businesses/{businessId}/warehouses](../../reference/warehouses/getPartnerWarehouses.md). [Что такое группы складов и зачем они нужны](https://yandex.ru/support/marketplace/assortment/operations/stocks.html#unified-stocks). {% endnote %} {% include notitle [limit](../../_auto/method_limits/getPagedWarehouses.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |

## Запрос

**Тело запроса** (`application/json`):

- `components` — array[string (ADDRESS, STATUS)]. Свойства складов, которые необходимо вернуть. Если какое-то значение параметра не задано, этой информации в ответе не будет. Передавайте параметр, только если нужна информация, которую он возвращает. Можно передать сразу несколько значений.
- `campaignIds` — array[integer<int64>]. Список идентификаторов кампании тех магазинов, склады которых необходимо вернуть. Их можно узнать с помощью запроса [GET v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете — нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**: * блок **Идентификатор кампании**; * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**. ⚠️ Не используйте вместо них идентификаторы магазинов, которые указаны в кабинете продавца на Маркете рядом с названием магазина и в некоторых отчетах.

## Ответы

**200** — Список складов и их свойства, которые вы запрашивали.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация о складах в кабинете.
  - `warehouses` — array[object] **обязательный**. Список складов.
    - `id` — integer<int64> **обязательный**. Идентификатор склада.
    - `name` — string **обязательный**. Название склада.
    - `campaignId` — integer<int64> **обязательный**. Идентификатор кампании того магазина, который связан со складом.
    - `express` — boolean **обязательный**. Возможна ли доставка для модели Экспресс.
    - `groupInfo` — object. Информация о группе, к которой принадлежит склад. Возвращается только для складов в группах. [Что такое группы складов и зачем они нужны](https://yandex.ru/support/marketplace/assortment/operations/stocks.html#unified-stocks)
      - `name` — string **обязательный**. Название группы, к которой принадлежит склад.
      - `id` — integer<int64> **обязательный**. Идентификатор группы складов.
    - `address` — object. Адрес склада. Возвращается, только если в запросе параметр `components` принимает значение `ADDRESS`.
      - `city` — string **обязательный**. Город.
      - `street` — string. Улица.
      - `number` — string. Номер дома.
      - `building` — string. Номер строения.
      - `block` — string. Номер корпуса.
      - `gps` — object **обязательный**. GPS-координаты широты и долготы.
        - `latitude` — number **обязательный**. Широта.
        - `longitude` — number **обязательный**. Долгота.
    - `status` — object. Статус склада. Возвращается, только если в запросе параметр `components` принимает значение `STATUS`. {% note info "Статус склада, полученный через API, может не совпадать со статусом в кабинете" %} Например, сначала Маркет отключил склад, а затем вы с помощью метода [POST v2/campaigns/{campaignId}/warehouse/status](../../reference/warehouses/updateWarehouseStatus.md). Статус в кабинете — **Отключен Маркетом**, а через API вернется **DISABLED_MANUALLY** (отключен вами). {% endnote %}
      - `status` — string (DISABLED_MANUALLY, OTHER) **обязательный**. Статус склада: * `DISABLED_MANUALLY` – отключен вами. * `OTHER` – другой статус. Например, склад включен или отключен Маркетом.
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
