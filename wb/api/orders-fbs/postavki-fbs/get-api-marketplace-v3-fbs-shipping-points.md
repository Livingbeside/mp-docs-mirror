---
title: Получить список пунктов отгрузки поставок
api: wb-orders-fbs
method: GET
path: /api/marketplace/v3/fbs/shipping-points
operation_id: getV3FbsShippingPoints
tags:
  - Поставки FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: c436b09867478299
---

# Получить список пунктов отгрузки поставок

`GET /api/marketplace/v3/fbs/shipping-points`

Описание метода

Метод возвращает доступные пункты отгрузки поставок с фильтрами:
 - по населённым пунктам России
 - по типам товаров, которые принимает пункт отгрузки

Используйте данные из этого метода, чтобы устанавливать [параметры отгрузки поставок](./orders-fbs#tag/Postavki-FBS/operation/patchV3FbsSuppliesShippingMethod).

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `city` | query | string | да | Населённый пункт отгрузки поставки, кириллица |
| `cargoType` | query | integer (1, 2, 3) | да | Тип товара, который принимает пункт отгрузки: - `1` — малогабаритный товар (МГТ) - `2` — сверхгабаритный товар (СГТ) - `3` — крупногабаритный товар (КГТ+) |

## Ответы

**200** — Успешно

- `shippingPoints` — array[object] **обязательный**. Список пунктов отгрузки
  - `id` — integer<int64> **обязательный**. ID пункта отгрузки
  - `name` — string **обязательный**. Название
  - `address` — string **обязательный**. Адрес
  - `city` — string **обязательный**. Населённый пункт
  - `officeType` — string (sc, sw, pp) **обязательный**. Тип пункта отгрузки: - `sc` — сортировочный центр - `sw` — склад - `pp` — ПВЗ
  - `cargoTypes` — array[integer (1, 2, 3)] **обязательный**. Типы товаров, которые принимает пункт отгрузки: - `1` — малогабаритный товар (МГТ) - `2` — сверхгабаритный товар (СГТ) - `3` — крупногабаритный товар (КГТ+)
  - `latitude` — number **обязательный**. Широта
  - `longitude` — number **обязательный**. Долгота
  - `fulfillment` — boolean **обязательный**. Услуга **Фулфилмент в СЦ** для поставки по модели FBS: - `true` — доступна - `false` — недоступна

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
