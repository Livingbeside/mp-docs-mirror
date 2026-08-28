---
title: Список товаров для участия в акции
api: wb-promotion
method: GET
path: /api/v1/calendar/promotions/nomenclatures
operation_id: getV1CalendarPromotionsNomenclatures
tags:
  - promoCalendar
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: b4d35b6fae3ae276
---

# Список товаров для участия в акции

`GET /api/v1/calendar/promotions/nomenclatures`

Описание метода

Метод формирует список товаров, подходящих для участия в [акции](./promotion#tag/promoCalendar/operation/getV1CalendarPromotionsDetails). Эти товары можно добавить в акцию с помощью [отдельного метода](./promotion#tag/promoCalendar/operation/postV1CalendarPromotionsUpload).

 Данный метод неприменим для автоакций.

Лимит запросов на один аккаунт продавца для всех методов категории Календарь акций:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 6 сек | 10 запросов | 600 мс | 5 запросов |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `promotionID` | query | integer | да | ID акции |
| `inAction` | query | boolean | да | Участвует в акции: - `true` — да - `false` — нет |
| `limit` | query | integer<uint> | нет | Количество запрашиваемых товаров |
| `offset` | query | integer<uint> | нет | После какого элемента выдавать данные |

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `nomenclatures` — array[object]. Список товаров
    - `currencyCode` — string. Валюта в формате ISO 4217
    - `discount` — integer. Текущая скидка
    - `id` — integer. Артикул WB
    - `inAction` — boolean. Участвует в акции: - `true` — да - `false` — нет
    - `planDiscount` — integer. Рекомендуемая скидка для участия в акции
    - `planPrice` — number<float>. Плановая цена (цена во время акции)
    - `price` — number<float>. Текущая розничная цена

**400** — Неправильный запрос

- `errorText` — string. Текст ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**402** — Требуется платёж

- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)
- `title` — string. Заголовок ошибки

**422** — Ошибка обработки параметров запроса

- `errorText` — string. Текст ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
