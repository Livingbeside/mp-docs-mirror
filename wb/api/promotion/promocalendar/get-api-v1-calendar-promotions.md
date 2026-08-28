---
title: Список акций
api: wb-promotion
method: GET
path: /api/v1/calendar/promotions
operation_id: getV1CalendarPromotions
tags:
  - promoCalendar
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: e39ac7e58d00f949
---

# Список акций

`GET /api/v1/calendar/promotions`

Описание метода

Метод возвращает список [акций](./promotion#tag/promoCalendar/operation/getV1CalendarPromotionsDetails) в WB с датами и временем проведения.

Лимит запросов на один аккаунт продавца для всех методов категории Календарь акций:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `startDateTime` | query | string<date-time> | да | Начало периода, формат `YYYY-MM-DDTHH:MM:SSZ` |
| `endDateTime` | query | string<date-time> | да | Конец периода, формат `YYYY-MM-DDTHH:MM:SSZ` |
| `allPromo` | query | boolean | да | Показать акции: - `false` — доступные для участия - `true` — все акции |
| `limit` | query | integer<uint> | нет | Количество запрашиваемых акций |
| `offset` | query | integer<uint> | нет | После какого элемента выдавать данные |

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `promotions` — array[object]. Список акций
    - `endDateTime` — string<date-time>. Конец акции
    - `id` — integer. ID акции
    - `name` — string. Название акции
    - `startDateTime` — string<date-time>. Начало акции
    - `type` — string (regular, auto). Тип акции: - `regular` — акция - `auto` — автоакция

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
