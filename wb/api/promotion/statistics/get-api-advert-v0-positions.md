---
title: Позиции карточек товаров в поисковой выдаче
api: wb-promotion
method: GET
path: /api/advert/v0/positions
operation_id: getV0Positions
tags:
  - statistics
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 52b32f9282ed3ee3
---

# Позиции карточек товаров в поисковой выдаче

`GET /api/advert/v0/positions`

Описание метода

Метод возвращает медианные позиции карточек товаров в поисковой выдаче и распределение показов по фиксированным диапазонам позиций.

 
Лимит запросов на один профиль продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 10 запросов | 6 сек | 1 запрос |
| Сервисный | 1 мин | 10 запросов | 6 сек | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `advertIds` | query | array[integer<int64>] | да | Список ID рекламных кампаний |
| `nmIds` | query | array[integer<int64>] | нет | Артикулы WB |
| `beginDate` | query | string<date> | да | Дата начала интервала |
| `endDate` | query | string<date> | да | Дата окончания интервала |

## Ответы

**200** — Успешно

- `rows` — ? **обязательный**
  - `advertId` — integer<int64> **обязательный**. ID рекламной кампании
  - `nmId` — integer<int64> **обязательный**. Артикул WB
  - `date` — string<date> **обязательный**. Дата, за которую представлены данные
  - `posMedian` — integer **обязательный**. Медианная позиция карточки товара в поиске с учётом буста
  - `posNoboostMedian` — integer **обязательный**. Медианная позиция карточки товара в поиске без учёта буста
  - `posMedianDiff` — integer **обязательный**. На сколько буст поднял карточку товара в выдаче: `posNoboostMedian` - `posMedian`
  - `ranges` — array[object] **обязательный**. Диапазоны
    - `range` — string (1-2, 3-10, 11-34, 35-50, 51-100, 101-300, 301+) **обязательный**. Диапазон позиций в поисковой выдаче
    - `views` — integer. Количество показов в диапазоне с учётом буста. Только для CPM-кампаний
    - `viewsShare` — number<double>. Доля показов диапазона от всех показов карточки товара за день, %. Только для CPM-кампаний
    - `viewsNoBoost` — integer. Количество показов в диапазоне без учёта буста. Только для CPM-кампаний
    - `clicks` — integer **обязательный**. Количество кликов в диапазоне
    - `clicksShare` — number<double> **обязательный**. Доля кликов диапазона от всех кликов по карточке товара за день, %
    - `ctr` — number<double> **обязательный**. Кликабельность — отношение числа кликов к количеству показов, %

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `request_id` — string **обязательный**. Уникальный ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

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
