---
title: Получить информацию о поставке{{ /api/v3/supplies/{supplyId} }}
api: wb-orders-fbs
method: GET
path: /api/v3/supplies/{supplyId}
operation_id: getV3SuppliesSupplyId
tags:
  - fbsSupplies
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 9dcb02299a32d993
---

# Получить информацию о поставке{{ /api/v3/supplies/{supplyId} }}

`GET /api/v3/supplies/{supplyId}`

Описание метода

Метод возвращает подробную информацию о поставке.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `supplyId` | path | string | да | ID поставки |

## Ответы

**200** — Успешно

- `id` — string. ID поставки
- `isB2b` — boolean. Признак B2B-продажи: - `true` — B2B-продажа - `false` — не B2B-продажа - `null` — признак отсутствует, сборочные задания не добавлены к поставке
- `isPickupPointShipmentAllowed` — boolean. Можно ли отгрузить заказ на ПВЗ: - `false` — нет - `true` — да
- `done` — boolean. Флаг закрытия поставки: - `true` — закрыта - `false` — открыта
- `createdAt` — string<date-time>. Дата создания поставки (RFC3339)
- `closedAt` — string<date-time>. Дата закрытия поставки (RFC3339)
- `scanDt` — string<date-time>. Дата сканирования поставки или первого заказа (RFC3339)
- `name` — string. Наименование поставки
- `cargoType` — integer (0, 1, 2, 3). Тип товара: - `1` — малогабаритный товар (МГТ) - `2` — сверхгабаритный товар (СГТ) - `3` — крупногабаритный товар (КГТ+)
- `crossBorderType` — integer (0, 1). Тип поставки: - `0` — внутренняя поставка - `1` — трансграничная поставка - `null` — значение отсутствует
- `destinationOfficeId` — integer<int64>. ID склада хранения сборочных заданий в поставке. Если `null`, склад не указан
- `recommendedWhId` — integer<int64>. ID рекомендуемого склада для приёмки поставки для Москвы и МО. Рекомендуется ближайший к покупателям склад, который определяется автоматически при передаче поставки в доставку с учётом параметров всех сборочных заданий в поставке. Если `0`, рекомендуемый склад не определён
- `shippingDt` — string. Планируемая дата отгрузки поставки, формат `YYYY-MM-DD`
- `shippingPointId` — integer. ID пункта отгрузки. Можно получить в методе получения [пунктов отгрузки поставок](./orders-fbs#tag/fbsSupplies/operation/getV3FbsShippingPoints)
- `shippingType` — string (selfShipping, transportCompany). Способ доставки до пункта отгрузки: - `selfShipping` — доставка силами продавца - `transportCompany` — доставка через транспортную компанию. Для этого способа обязательно укажите ID ЭТрН — электронной транспортной накладной — в поле `waybillUuid`
- `waybillUuid` — string. ID ЭТрН — электронной транспортной накладной. Обязателен при `"shippingType":"transportCompany"`
- `spotAvailable` — boolean **обязательный**. Доступен ли СПОТ для этой поставки: - `true` — да. Используйте метод [получения данных СПОТ](./orders-fbs#tag/fbsSupplies/operation/postV3FbsSuppliesSpotList) - `false` — нет

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

**402** — Требуется платёж

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)

**403** — Доступ запрещён

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**404** — Не найдено

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
