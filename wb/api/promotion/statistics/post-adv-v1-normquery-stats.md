---
title: Статистика по поисковым кластерам с детализацией по дням
api: wb-promotion
method: POST
path: /adv/v1/normquery/stats
operation_id: postV1NormqueryStats
tags:
  - statistics
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 051f063c922b30ea
---

# Статистика по поисковым кластерам с детализацией по дням

`POST /adv/v1/normquery/stats`

Описание метода

Метод формирует статистику по поисковым кластерам за указанный период с детализацией по дням.
Можно использовать для кампаний с моделями оплаты `cpm` — за показы и `cpc` — за клики.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 10 запросов | 6 сек | 20 запросов |
| Сервисный | 1 мин | 10 запросов | 6 сек | 20 запросов |
| Базовый с секретом | 1 мин | 10 запросов | 6 сек | 20 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `from` — string<date> **обязательный**. Дата начала периода
- `items` — array[object] **обязательный**
  - `advertId` — integer<int64> **обязательный**. ID кампании
  - `nmId` — integer<int64> **обязательный**. Артикул WB
- `to` — string<date> **обязательный**. Дата окончания периода периода

## Ответы

**200** — Успешно

- `items` — array[object] **обязательный**
  - `advertId` — integer<int64> **обязательный**. ID кампании
  - `dailyStats` — array[object]. Статистика с детализацией по дням
    - `date` — string<date> **обязательный**. Дата
    - `stat` — object
      - `atbs` — integer. Количество добавлений товаров в корзину
      - `avgPos` — number<float>. Средняя позиция товара на страницах поисковой выдачи
      - `clicks` — integer. Количество кликов
      - `cpc` — number<float>. Средняя стоимость клика в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
      - `cpm` — number<float>. Средняя стоимость за тысячу показов в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances). Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`
      - `ctr` — number<float>. CTR (click-through rate) — отношение числа кликов к количеству показов в процентах. Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`
      - `normQuery` — string. Поисковый кластер
      - `orders` — integer. Количество заказов
      - `shks` — integer. Количество заказанных товаров, шт.
      - `spend` — number<double>. Затраты на продвижение товаров в конкретном поисковом кластере кампании
      - `views` — integer. Количество просмотров. Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`
  - `nmId` — integer<int64> **обязательный**. Артикул WB

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `request_id` — string **обязательный**. Уникальный ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

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
