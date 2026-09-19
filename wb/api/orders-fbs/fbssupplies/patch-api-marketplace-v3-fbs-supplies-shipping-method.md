---
title: Установить параметры отгрузки поставок
api: wb-orders-fbs
method: PATCH
path: /api/marketplace/v3/fbs/supplies/shipping-method
operation_id: patchV3FbsSuppliesShippingMethod
tags:
  - fbsSupplies
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 268272f3f038b3f3
---

# Установить параметры отгрузки поставок

`PATCH /api/marketplace/v3/fbs/supplies/shipping-method`

Описание метода

Метод устанавливает способ доставки, дату и пункт отгрузки у поставок.

Для доставки транспортной компанией `"shippingType":"transportCompany"` укажите ID ЭТрН — электронной транспортной накладной — с помощью метода установки [ID ЭТрН поставки](./orders-fbs#tag/fbsSupplies/operation/patchV3FbsSuppliesWaybill).

 Добавленный к поставке ID ЭТрН сбрасывается, если поменять способ доставки "shippingType":"transportCompany" на selfShipping. Если вы хотите изменить способ доставки обратно на transportCompany, добавьте ID ЭТрН заново.

Вы можете обновлять параметры отгрузки до сканирования поставки и её коробов в пункте отгрузки. Когда поставка будет отсканирована, метод начнёт возвращать ошибку `409`.

В запросе можно указать максимум 100 поставок. Результат обработки возвращается для каждой поставки отдельно.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `data` — array[object] **обязательный**
  - `shippingDt` — string **обязательный**. Планируемая дата отгрузки поставки, формат `YYYY-MM-DD`
  - `shippingPointId` — integer **обязательный**. ID пункта отгрузки. Можно получить с помощью [отдельного метода](./orders-fbs#tag/fbsSupplies/operation/getV3FbsShippingPoints)
  - `shippingType` — string (selfShipping, transportCompany) **обязательный**. Способ доставки до пункта отгрузки: - `selfShipping` — доставка силами продавца - `transportCompany` — доставка через транспортную компанию. Для этого способа обязательно [укажите ID ЭТрН](./orders-fbs#tag/fbsSupplies/operation/patchV3FbsSuppliesWaybill) — электронной транспортной накладной — в поле `waybillUuid`
  - `supplyId` — string **обязательный**. ID поставки

## Ответы

**200** — Успешно

- `results` — array[object] **обязательный**
  - `error` — object. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки
    - `detail` — string **обязательный**. Дополнительная информация об ошибке
  - `success` — boolean. Успешна ли обработка запроса для данной поставки. Может быть только `true`
  - `supplyId` — string **обязательный**. ID поставки

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

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**409** — Конфликт

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
