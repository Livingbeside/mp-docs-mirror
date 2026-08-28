---
title: Статистика поисковых кластеров
api: wb-promotion
method: POST
path: /adv/v0/normquery/stats
operation_id: postV0NormqueryStats
tags:
  - statistics
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: ca5987cbdffa2c3a
---

# Статистика поисковых кластеров

`POST /adv/v0/normquery/stats`

Описание метода

Метод формирует статистику по поисковым кластерам за указанный период.

Можно использовать для кампаний с моделями оплаты `cpm` — за показы и `cpc` — за клики.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 10 запросов | 6 сек | 20 запросов |
| Сервисный | 1 мин | 10 запросов | 6 сек | 20 запросов |
| Базовый с секретом | 1 мин | 10 запросов | 6 сек | 20 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `from` — string<date> **обязательный**. Дата начала периода
- `to` — string<date> **обязательный**. Дата окончания периода
- `items` — array[object] **обязательный**
  - `advert_id` — integer **обязательный**. ID кампании
  - `nm_id` — integer **обязательный**. Артикул WB

## Ответы

**200** — Успешно

- `stats` — array[object] **обязательный**
  - `advert_id` — integer **обязательный**. ID кампании
  - `nm_id` — integer **обязательный**. Артикул WB
  - `stats` — array[object]
    - `norm_query` — string. Поисковый кластер
    - `views` — integer. Количество просмотров. Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`
    - `clicks` — integer. Количество кликов
    - `atbs` — integer. Количество добавлений товаров в корзину
    - `orders` — integer. Количество заказов
    - `ctr` — number<double>. Кликабельность — отношение числа кликов к количеству показов, %. Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`
    - `cpc` — number<double>. Стоимость одного клика в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
    - `cpm` — number<double>. Средняя стоимость за тысячу показов в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances). Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`
    - `avg_pos` — number<double>. Средняя позиция товара на страницах поисковой выдачи
    - `shks` — integer. Количество заказанных товаров, шт.
    - `spend` — number<double>. Затраты на продвижение товаров в конкретном поисковом кластере кампании
    - `currency` — string<ISO 4217>. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)

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

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `request_id` — string **обязательный**. Уникальный ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
