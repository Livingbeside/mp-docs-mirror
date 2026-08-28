---
title: Статусы проверки кодов маркировки
api: yandex-market
method: POST
path: /v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status
operation_id: getOrderIdentifiersStatus
tags:
  - orders
  - fbs
  - express
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: a70719f4e4aa8279
---

# Статусы проверки кодов маркировки

`POST /v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status`

{% include notitle [access](../../_auto/method_scopes/getOrderIdentifiersStatus.md) %} Возвращает статусы проверки кодов маркировки в заказе. Заказ, в котором есть ювелирные изделия или товары с обязательной маркировкой в системе [«Честный ЗНАК»](https://честныйзнак.рф/), можно перевести в статус `READY_TO_SHIP`, только когда: 1. В методе [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](../../reference/orders/setOrderBoxLayout.md) вы передадите Маркету: * [УИНы](:no-translate[*uin]) по каждому ювелирному изделию в заказе; * коды маркировки в системе :no-translate[«Честный ЗНАК»] по всем товарам в заказе, для которых она обязательна. 2. Все коды маркировки успешно пройдут проверку. {% include notitle [limit](../../_auto/method_limits/getOrderIdentifiersStatus.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `campaignId` | path | integer<int64> | да | Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия. Его можно узнать с помощью запроса [GET v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**: * блок **Идентификатор кампании**; * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**. ⚠️ Не путайте его с: - идентификатором магазина, который отображается в личном кабинете продавца; - рекламными кампаниями. |
| `orderId` | path | integer<int64> | да | Идентификатор заказа. |

## Ответы

**200** — Информация по проверке кодов маркировки.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация по проверке кодов маркировки.
  - `items` — array[object] **обязательный**. Список идентификаторов товаров и информация по проверке кодов.
    - `id` — integer<int64> **обязательный**. Идентификатор товара в заказе.
    - `uin` — array[object]. Информация по проверке :no-translate[УИНов].
      - `value` — string **обязательный**. УИН товара.
      - `status` — string (OK, IN_PROGRESS, FAILED, NOT_ON_VALIDATION) **обязательный**. Статус проверки УИНа: * `FAILED` — не прошел проверку. * `IN_PROGRESS` — в процессе проверки. * `NOT_ON_VALIDATION` — УИН не отправлен на проверку или переданы не все УИНы в заказе. * `OK` — проверка успешно пройдена.
      - `substatus` — string (UIN_MERCHANT_MISMATCH, UIN_MERCHANT_UNREGISTERED, UIN_NO_DATA). Детализация ошибки при проверке :no-translate[УИНа]. * `UIN_MERCHANT_MISMATCH` — :no-translate[УИН] не принадлежит вашему магазину. * `UIN_MERCHANT_UNREGISTERED` — магазин не подключен к системе :no-translate[ГИИС ДМДК]. * `UIN_NO_DATA` — :no-translate[УИН] не найден или заблокирован. Возвращается только для статуса `FAILED`.
    - `cis` — array[object]. Информация по проверке кодов маркировки в системе :no-translate[«Честный ЗНАК»].
      - `value` — string **обязательный**. Код маркировки в системе :no-translate[«Честный ЗНАК»].
      - `status` — string (OK, FAILED, IN_PROGRESS, INVALID, NOT_ON_VALIDATION) **обязательный**. Статус проверки кода маркировки в системе :no-translate[«Честный ЗНАК»]: * `FAILED` — не удалось проверить код. Повторите попытку позже или удалите код маркировки. * `IN_PROGRESS` — в процессе проверки. * `NOT_ON_VALIDATION` — код маркировки не отправлен на проверку. * `OK` — проверка успешно пройдена. * `INVALID` — проверка не пройдена. Продажа товара с этим кодом запрещена.
      - `substatus` — string (WRONG_OWNER_INN, CIS_VALIDATION_ERROR, CIS_GTIN_NOT_FOUND, CIS_SERIAL_NUMBER_NOT_FOUND, INVALID_SYMBOLS_FOUND, CRYPTO_TAIL_FORMAT_MISMATCH_CIS_TYPE, INVALID_CRYPTO_TAIL, INVALID_CRYPTO_KEY, VERIFICATION_FAILED_IN_EMITTER_COUNTRY, UNSUPPORTED_AI_FOUND, CIS_NOT_FOUND_IN_GIS_MT, NOT_PLACED_ON_MARKET…). Детализация ошибки при проверке кода маркировки в системе :no-translate[«Честный ЗНАК»]: * `WRONG_OWNER_INN` — проверка не пройдена. ИНН владельца кода отличается от ИНН продавца. * `CIS_VALIDATION_ERROR` — проверка не пройдена. * `CIS_GTIN_NOT_FOUND` — код маркировки не содержит [GTIN](:no-translate[*gtin]). * `CIS_SERIAL_NUMBER_NOT_FOUND` — код маркировки не содержит серийный номер. * `INVALID_SYMBOLS_FOUND` — код маркировки содержит недопустимые символы. * `CRYPTO_TAIL_FORMAT_MISMATCH_CIS_TYPE` — формат криптоподписи не соответствует типу кода маркировки. * `INVALID_CRYPTO_TAIL` — криптоподпись не валидна. * `INVALID_CRYPTO_KEY` — криптоключ не валиден. * `VERIFICATION_FAILED_IN_EMITTER_COUNTRY` — код маркировки не прошел верификацию в стране эмитента. * `UNSUPPORTED_AI_FOUND` — найденные в коде маркировки AI не поддерживаются. * `CIS_NOT_FOUND_IN_GIS_MT` — код маркировки не найден в :no-translate[ГИС МТ]. * `NOT_PLACED_ON_MARKET` — код маркировки не введен в оборот. * `NOT_PRINTED_ON_PACKAGE` — код маркировки не нанесен на упаковку. * `EXPIRED_ITEM` — у маркированного товара истек срок годности. * `SALE_BLOCKED_BY_OGB` — розничная продажа продукции заблокирована по решению ОГВ. * `ITEM_SOLD` — маркированный товар был продан. Возвращается только для статуса `INVALID`.
      - `crptRequestId` — string. **Только для модели LaaS** Идентификатор запроса проверки кода маркировки в [ЦРПТ](https://crpt.ru/), на основании которой принято решение о продаже товара.
      - `crptRequestDateTime` — string<date-time>. **Только для модели LaaS** Время проверки кода маркировки в [ЦРПТ](https://crpt.ru/), на основании которой принято решение о продаже товара.

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
