---
title: Предметы для кампаний
api: wb-promotion
method: GET
path: /adv/v1/supplier/subjects
operation_id: getV1SupplierSubjects
tags:
  - creatingCampaigns
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: cf9a569c1c7473f1
---

# Предметы для кампаний

`GET /adv/v1/supplier/subjects`

Описание метода

Метод возвращает список [предметов](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2ObjectAll), которые можно добавить в рекламную [кампанию](./promotion#tag/campaigns/operation/getV2Adverts).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 12 сек | 1 запрос | 12 сек | 5 запросов |
| Сервисный | 12 сек | 1 запрос | 12 сек | 5 запросов |
| Базовый с секретом | 12 сек | 1 запрос | 12 сек | 5 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `payment_type` | query | string | нет | Тип оплаты: - `cpm` — за показы - `cpc` — за клик |

## Ответы

**200** — Успешно

- `id` — integer. ID предмета
- `name` — string. Предмет
- `count` — integer. Количество Артикулов WB (`nmId`) с таким предметом.

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

**404** — Не найдено

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
