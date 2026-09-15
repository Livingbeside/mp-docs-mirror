---
title: Добавить товар в акцию
api: wb-promotion
method: POST
path: /api/v1/calendar/promotions/upload
operation_id: postV1CalendarPromotionsUpload
tags:
  - promoCalendar
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 61b4707450abdb30
---

# Добавить товар в акцию

`POST /api/v1/calendar/promotions/upload`

Описание метода

Метод создаёт задание на загрузку товара в [акцию](./promotion#tag/promoCalendar/operation/getV1CalendarPromotionsDetails).

Состояние загрузки можно проверить с помощью [отдельных методов](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryTasks).

 Данный метод неприменим для автоакций.

Лимит запросов на один аккаунт продавца для всех методов категории Календарь акций:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `data` — object. Данные запроса
  - `promotionID` — integer. ID акции
  - `uploadNow` — boolean. Установить скидку: - `true` — сейчас - `false` — в момент старта акции
  - `nomenclatures` — array[integer]. Артикулы WB, которые можно добавить в акцию

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `alreadyExists` — boolean. Загрузка с такими данными уже существует
  - `uploadID` — integer. ID загрузки

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

**403** — Доступ запрещён

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

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
