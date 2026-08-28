---
title: Список товаров для участия в акции{{ /api/v1/calendar/promotions/nomenclatures }}
api: wb-promotion
method: GET
path: /api/v1/calendar/promotions/nomenclatures
operation_id: getV1CalendarPromotionsNomenclatures
tags:
  - promoCalendar
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: aa8b69313b99c8ef
---

# Список товаров для участия в акции{{ /api/v1/calendar/promotions/nomenclatures }}

`GET /api/v1/calendar/promotions/nomenclatures`

Описание метода Метод формирует список товаров, подходящих для участия в [акции](./promotion#tag/promoCalendar/operation/getV1CalendarPromotionsDetails). Эти товары можно добавить в акцию с помощью [отдельного метода](./promotion#tag/promoCalendar/operation/postV1CalendarPromotionsUpload). Данный метод неприменим для автоакций. Лимит запросов на один аккаунт продавца для всех методов категории Календарь акций : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 6 сек | 10 запросов | 600 мс | 5 запросов |

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
    - `id` — integer. Артикул WB
    - `inAction` — boolean. Участвует в акции: - `true` — да - `false` — нет
    - `price` — number<float>. Текущая розничная цена
    - `currencyCode` — string. Валюта в формате ISO 4217
    - `planPrice` — number<float>. Плановая цена (цена во время акции)
    - `discount` — integer. Текущая скидка
    - `planDiscount` — integer. Рекомендуемая скидка для участия в акции

**400** — Неправильный запрос

- `errorText` — string. Текст ошибки

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

**422** — Ошибка обработки параметров запроса

- `errorText` — string. Текст ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
