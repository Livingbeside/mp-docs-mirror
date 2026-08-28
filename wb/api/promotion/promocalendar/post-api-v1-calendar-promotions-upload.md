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
content_sha: 635124f2f9eeefe3
---

# Добавить товар в акцию

`POST /api/v1/calendar/promotions/upload`

Описание метода

Метод создаёт задание на загрузку товара в [акцию](./promotion#tag/promoCalendar/operation/getV1CalendarPromotionsDetails).

Состояние загрузки можно проверить с помощью [отдельных методов](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1history~1tasks/get).

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
  - `nomenclatures` — array[integer]. Артикулы WB, которые можно добавить в акцию
  - `promotionID` — integer. ID акции
  - `uploadNow` — boolean. Установить скидку: - `true` — сейчас - `false` — в момент старта акции

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `alreadyExists` — boolean. Загрузка с такими данными уже существует
  - `uploadID` — integer. ID загрузки

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
