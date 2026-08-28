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
content_sha: f4c046485fb2d480
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
- `items` — array[object] **обязательный**
  - `advert_id` — integer **обязательный**. ID кампании
  - `nm_id` — integer **обязательный**. Артикул WB
- `to` — string<date> **обязательный**. Дата окончания периода

## Ответы

**200** — Успешно

- `stats` — array[object] **обязательный**
  - `advert_id` — integer **обязательный**. ID кампании
  - `nm_id` — integer **обязательный**. Артикул WB
  - `stats` — array[object]
    - `atbs` — integer. Количество добавлений товаров в корзину
    - `avg_pos` — number<double>. Средняя позиция товара на страницах поисковой выдачи
    - `clicks` — integer. Количество кликов
    - `cpc` — number<double>. Стоимость одного клика в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
    - `cpm` — number<double>. Средняя стоимость за тысячу показов в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances). Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`
    - `ctr` — number<double>. Кликабельность — отношение числа кликов к количеству показов, %. Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`
    - `currency` — string<ISO 4217>. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
    - `norm_query` — string. Поисковый кластер
    - `orders` — integer. Количество заказов
    - `shks` — integer. Количество заказанных товаров, шт.
    - `spend` — number<double>. Затраты на продвижение товаров в конкретном поисковом кластере кампании
    - `views` — integer. Количество просмотров. Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`

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

**403** — Доступ запрещён

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `request_id` — string **обязательный**. Уникальный ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
