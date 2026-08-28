---
title: Статистика по поисковым кластерам с детализацией по дням{{ /adv/v1/normquery/stats }}
api: wb-promotion
method: POST
path: /adv/v1/normquery/stats
operation_id: postV1NormqueryStats
tags:
  - statistics
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: fb0bd02c4e223c6d
---

# Статистика по поисковым кластерам с детализацией по дням{{ /adv/v1/normquery/stats }}

`POST /adv/v1/normquery/stats`

Описание метода Метод формирует статистику по поисковым кластерам за указанный период с детализацией по дням. Можно использовать для кампаний с моделями оплаты `cpm` — за показы и `cpc` — за клики. Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 10 запросов | 6 сек | 20 запросов | | Сервисный | 1 мин | 10 запросов | 6 сек | 20 запросов | | Базовый с секретом | 1 мин | 10 запросов | 6 сек | 20 запросов | | Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `from` — string<date> **обязательный**. Дата начала периода
- `to` — string<date> **обязательный**. Дата окончания периода периода
- `items` — array[object] **обязательный**
  - `advertId` — integer<int64> **обязательный**. ID кампании
  - `nmId` — integer<int64> **обязательный**. Артикул WB

## Ответы

**200** — Успешно

- `items` — array[object] **обязательный**
  - `advertId` — integer<int64> **обязательный**. ID кампании
  - `nmId` — integer<int64> **обязательный**. Артикул WB
  - `dailyStats` — array[object]. Статистика с детализацией по дням
    - `date` — string<date> **обязательный**. Дата
    - `stat` — object
      - `normQuery` — string. Поисковый кластер
      - `views` — integer. Количество просмотров. Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`
      - `clicks` — integer. Количество кликов
      - `atbs` — integer. Количество добавлений товаров в корзину
      - `orders` — integer. Количество заказов
      - `ctr` — number<float>. CTR (click-through rate) — отношение числа кликов к количеству показов в процентах. Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`
      - `cpc` — number<float>. Средняя стоимость клика в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
      - `cpm` — number<float>. Средняя стоимость за тысячу показов в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances). Для кампаний с типом оплаты `cpc` — за клики — значение будет `null`
      - `avgPos` — number<float>. Средняя позиция товара на страницах поисковой выдачи
      - `shks` — integer. Количество заказанных товаров, шт.
      - `spend` — number<double>. Затраты на продвижение товаров в конкретном поисковом кластере кампании

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
