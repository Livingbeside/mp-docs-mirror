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
content_sha: 57c15ff9563fd440
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
  - `type` — integer. Тип кампании: - `8` — кампания с единой ставкой (**устаревший тип**) - `9` — кампания с единой или ручной ставкой. Тип ставки вы можете получить с помощью метода [Информация о кампаниях](./promotion#tag/campaigns/operation/getV2Adverts), поле `bid_type`
  - `status` — integer. Статус кампании
  - `count` — integer. Количество кампаний
  - `advert_list` — array[object]. Список кампаний
    - `advertId` — integer. ID кампании
    - `changeTime` — string<date-time>. Дата и время последнего изменения кампании
- `all` — integer. Общее количество кампаний всех статусов и типов

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
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
