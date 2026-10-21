---
title: Получить список пунктов отгрузки поставки{{ /api/marketplace/v3/fbs/supplies/{supplyId}/shipping-points }}
api: wb-orders-fbs
method: GET
path: /api/marketplace/v3/fbs/supplies/{supplyId}/shipping-points
operation_id: getV3FbsSuppliesSupplyIdShippingPoints
tags:
  - fbsSupplies
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 446446a9bde9410e
---

# Получить список пунктов отгрузки поставки{{ /api/marketplace/v3/fbs/supplies/{supplyId}/shipping-points }}

`GET /api/marketplace/v3/fbs/supplies/{supplyId}/shipping-points`

Описание метода

Метод возвращает доступные пункты отгрузки для указанной поставки.

Используйте данные этого метода, чтобы устанавливать [параметры отгрузки поставок](./orders-fbs#tag/fbsSupplies/operation/patchV3FbsSuppliesShippingMethod).

Лимит запросов на один профиль продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `supplyId` | path | string | да | ID поставки |
| `city` | query | string | да | Населённый пункт отгрузки поставки, кириллица |
| `officeType` | query | string | да | Тип пункта отгрузки. Укажите значения через запятую: - `sc` — сортировочный центр - `sw` — склад - `pp` — пункт выдачи заказов (ПВЗ) - `pfc` — партнёрский фулфилмент-центр (ПФЦ) - `gpp` — пункт приёма товаров (ППТ) |
| `shippingDt` | query | string | нет | Планируемая дата отгрузки поставки в формате `YYYY-MM-DD`. Обязательно для заказов МГТ (`"cargoType":1`) и КГТ+ (`"cargoType":3`). Если значение передано, в ответе возвращаются только пункты отгрузки, в которые можно отгрузить поставку в указанную дату |

## Ответы

**200** — Успешно

- `shippingPoints` — array[object] **обязательный**. Список пунктов отгрузки для указанной поставки
  - `id` — integer<int64> **обязательный**. ID пункта отгрузки
  - `name` — string **обязательный**. Название
  - `address` — string **обязательный**. Адрес
  - `city` — string **обязательный**. Населённый пункт
  - `officeType` — string **обязательный**. Тип пункта отгрузки: - `sc` — сортировочный центр - `sw` — склад - `pp` — пункт выдачи заказов (ПВЗ) - `pfc` — партнёрский фулфилмент-центр (ПФЦ) - `gpp` — пункт приёма товаров (ППТ)
  - `latitude` — number **обязательный**. Широта
  - `longitude` — number **обязательный**. Долгота
  - `fulfillment` — boolean **обязательный**. Услуга **Фулфилмент в СЦ** для поставки по модели FBS: - `true` — доступна - `false` — недоступна
  - `available` — boolean **обязательный**. Доступен ли пункт для отгрузки поставки: - `true` — доступен - `false` — недоступен. Возвращается для ПВЗ, если ПВЗ перегружен в планируемую дату отгрузки

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**403** — Доступ запрещён

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**404** — Поставка не найдена

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**409** — В поставке нет сборочных заданий

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
