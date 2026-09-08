---
title: Статистика медиакампаний
api: wb-promotion
method: POST
path: /adv/v1/stats
operation_id: postV1Stats
tags:
  - statistics
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 42e7ec401333a571
---

# Статистика медиакампаний

`POST /adv/v1/stats`

Описание метода

Метод формирует статистику кампаний сервиса [WB Медиа](https://cmp.wildberries.ru/cmpf/statistics). Статистику можно группировать по датам и/или интервалам.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 10 запросов | 100 мс | 10 запросов |
| Сервисный | 1 сек | 10 запросов | 100 мс | 10 запросов |
| Базовый с секретом | 1 сек | 10 запросов | 100 мс | 10 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `id` — integer **обязательный**. ID кампании
- `dates` — array[string<date>] **обязательный**. Даты, за которые нужно получить информацию
- `id` — integer **обязательный**. ID кампании
- `interval` — object **обязательный**. Временной диапазон, за который необходимо выдать данные
  - `begin` — string<date>. Начало запрашиваемого периода
  - `end` — string<date>. Конец запрашиваемого периода
- `id` — integer **обязательный**. ID кампании

## Ответы

**200** — Успешно

- `interval` — object **обязательный**. Период
  - `begin` — string<date>. Начало периода
  - `end` — string<date>. Конец периода
- `stats` — array[object]. Блок статистики
  - `item_id` — integer. ID баннера
  - `item_name` — string. Бренд
  - `category_name` — string. Название категории
  - `advert_type` — integer. Тип медиакампании: - `1` — размещение по дням - `2` — размещение по просмотрам
  - `place` — integer. Место на странице
  - `views` — integer. Количество просмотров
  - `clicks` — integer. Количество кликов
  - `cr` — number. CR(conversion rate) — это отношение количества заказов к общему количеству посещений медиакампании
  - `ctr` — number. CTR (click-through rate) — показатель кликабельности, отношение числа кликов к количеству показов в рамках медиакампании
  - `date_from` — string<date-time>. Время начала размещения
  - `date_to` — string<date-time>. Время завершения размещения
  - `subject_name` — string. Родительская категория предмета
  - `atbs` — integer. Количество добавлений товаров в корзину
  - `orders` — integer. Количество заказов
  - `price` — number. Стоимость размещения
  - `cpc` — number. (cost per click) — цена клика по продвигаемому товару
  - `status` — integer. Статус медиакампании
  - `daily_stats` — array[object]
    - `date` — string<date-time>. Дата
    - `app_type_stats` — array[object]. Статистика по платформам
      - `app_type` — integer. Тип платформы: - `1` — сайт - `32` — Android - `64` — IOS
      - `stats` — array[object]
        - `views` — integer. Количество просмотров
        - `clicks` — integer. Количество кликов
        - `atbs` — integer. Количество добавлений товаров в корзину
        - `ctr` — number. CTR (click-through rate) — показатель кликабельности, отношение числа кликов к количеству показов в рамках медиакампании
  - `expenses` — number. Стоимость размещения баннера
  - `cr1` — number. Отношение количества добавлений в корзину к количеству кликов
  - `cr2` — integer. Отношение количества заказов к количеству добавлений в корзину
- `dates` — array[string<date>] **обязательный**. Даты, за которые нужно получить информацию
- `stats` — array[object]. Блок статистики
  - `item_id` — integer. ID баннера
  - `item_name` — string. Бренд
  - `category_name` — string. Название категории
  - `advert_type` — integer. Тип медиакампании: - `1` — размещение по дням - `2` — размещение по просмотрам
  - `place` — integer. Место на странице
  - `views` — integer. Количество просмотров
  - `clicks` — integer. Количество кликов
  - `cr` — number. CR(conversion rate) — это отношение количества заказов к общему количеству посещений медиакампании
  - `ctr` — number. CTR (click-through rate) — показатель кликабельности, отношение числа кликов к количеству показов в рамках медиакампании
  - `date_from` — string<date-time>. Время начала размещения
  - `date_to` — string<date-time>. Время завершения размещения
  - `subject_name` — string. Родительская категория предмета
  - `atbs` — integer. Количество добавлений товаров в корзину
  - `orders` — integer. Количество заказов
  - `price` — number. Стоимость размещения
  - `cpc` — number. (cost per click) — цена клика по продвигаемому товару
  - `status` — integer. Статус медиакампании
  - `daily_stats` — array[object]
    - `date` — string<date-time>. Дата
    - `app_type_stats` — array[object]. Статистика по платформам
      - `app_type` — integer. Тип платформы: - `1` — сайт - `32` — Android - `64` — IOS
      - `stats` — array[object]
        - `views` — integer. Количество просмотров
        - `clicks` — integer. Количество кликов
        - `atbs` — integer. Количество добавлений товаров в корзину
        - `orders` — integer. Количество заказов
        - `cr` — number. CR(conversion rate) — отношение количества заказов к общему количеству посещений медиакампании
        - `ctr` — number. CTR (click-through rate) — показатель кликабельности, отношение числа кликов к количеству показов в рамках медиакампании
  - `expenses` — number. Стоимость размещения баннера
  - `cr1` — number. Отношение количества добавлений в корзину к количеству кликов
  - `cr2` — integer. Отношение количества заказов к количеству добавлений в корзину
- `stats` — array[object]. Блок статистики
  - `item_id` — integer. ID баннера
  - `item_name` — string. Бренд
  - `category_name` — string. Название категории
  - `advert_type` — integer. Тип медиакампании: - `1` — размещение по дням - `2` — размещение по просмотрам
  - `place` — integer. Место на странице
  - `views` — integer. Количество просмотров
  - `clicks` — integer. Количество кликов
  - `cr` — number. CR(conversion rate) — это отношение количества заказов к общему количеству посещений медиакампании
  - `ctr` — number. CTR (click-through rate) — показатель кликабельности, отношение числа кликов к количеству показов в рамках медиакампании
  - `date_from` — string<date-time>. Время начала размещения
  - `date_to` — string<date-time>. Время завершения размещения
  - `subject_name` — string. Родительская категория предмета
  - `atbs` — integer. Количество добавлений товаров в корзину
  - `orders` — integer. Количество заказов
  - `price` — number. Стоимость размещения
  - `cpc` — number. (cost per click) — цена клика по продвигаемому товару
  - `status` — integer. Статус медиакампании
  - `daily_stats` — array[object]
    - `date` — string<date-time>. Дата
    - `app_type_stats` — array[object]. Статистика по платформам
      - `app_type` — integer. Тип платформы: - `1` — сайт - `32` — Android - `64` — IOS
      - `stats` — array[object]
        - `views` — integer. Количество просмотров
        - `clicks` — integer. Количество кликов
        - `atbs` — integer. Количество добавлений товаров в корзину
        - `ctr` — number. CTR (click-through rate) — показатель кликабельности, отношение числа кликов к количеству показов в рамках медиакампании
  - `expenses` — number. Стоимость размещения баннера
  - `cr1` — number. Отношение количества добавлений в корзину к количеству кликов
  - `cr2` — integer. Отношение количества заказов к количеству добавлений в корзину
- `advert_id` — integer<int64>. ID кампании
- `error` — string. Описание ошибки

**400** — Неправильный запрос

- `error` — string

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
