---
title: Списки кампаний
api: wb-promotion
method: GET
path: /adv/v1/promotion/count
operation_id: getV1PromotionCount
tags:
  - campaigns
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: dbf7b83f179650d6
---

# Списки кампаний

`GET /adv/v1/promotion/count`

Описание метода

Метод возвращает списки всех [рекламных кампаний](./promotion#tag/campaigns/operation/getV2Adverts) продавца с их ID. Кампании сгруппированы по типу и статусу, у каждой указана дата последнего изменения.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Сервисный | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Базовый с секретом | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос |

## Ответы

**200** — Успешно

- `adverts` — array[object]. Данные по кампаниям
  - `advert_list` — array[object]. Список кампаний
    - `advertId` — integer. ID кампании
    - `changeTime` — string<date-time>. Дата и время последнего изменения кампании
  - `count` — integer. Количество кампаний
  - `status` — integer. Статус кампании
  - `type` — integer. Тип кампании: - `8` — кампания с единой ставкой (**устаревший тип**) - `9` — кампания с единой или ручной ставкой. Тип ставки вы можете получить с помощью метода [Информация о кампаниях](./promotion#tag/campaigns/operation/getV2Adverts), поле `bid_type`
- `all` — integer. Общее количество кампаний всех статусов и типов

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
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
