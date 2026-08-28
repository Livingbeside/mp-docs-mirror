---
title: Карточки товаров для кампаний
api: wb-promotion
method: POST
path: /adv/v2/supplier/nms
operation_id: postV2SupplierNms
tags:
  - creatingCampaigns
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 7a83105ad45a8835
---

# Карточки товаров для кампаний

`POST /adv/v2/supplier/nms`

Описание метода

Метод возвращает список [карточек товаров](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1list/post), которые можно добавить в рекламную [кампанию](./promotion#tag/campaigns/operation/getV2Adverts). Для получения карточек необходимы ID [предметов](./promotion#tag/creatingCampaigns/operation/getV1SupplierSubjects), также доступных для добавления в кампанию.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 5 запросов | 12 сек | 5 запросов |
| Сервисный | 1 мин | 5 запросов | 12 сек | 5 запросов |
| Базовый с секретом | 1 мин | 5 запросов | 12 сек | 5 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Успешно

- `nm` — integer. Артикул WB
- `subjectId` — integer. ID предмета
- `title` — string. Название товара

**400** — Неправильный запрос

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
