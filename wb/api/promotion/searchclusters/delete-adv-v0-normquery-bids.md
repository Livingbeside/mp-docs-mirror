---
title: Удалить ставки поисковых кластеров{{ /adv/v0/normquery/bids }}
api: wb-promotion
method: DELETE
path: /adv/v0/normquery/bids
operation_id: deleteV0NormqueryBids
tags:
  - searchClusters
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 32997c38952f621b
---

# Удалить ставки поисковых кластеров{{ /adv/v0/normquery/bids }}

`DELETE /adv/v0/normquery/bids`

Описание метода Метод удаляет ставки с поисковых кластеров. Можно использовать только для кампаний с: - ручной ставкой - моделью оплаты `cpm` — за показы Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 сек | 5 запросов | 200 мс | 10 запросов | | Сервисный | 1 сек | 5 запросов | 200 мс | 10 запросов | | Базовый с секретом | 1 сек | 5 запросов | 200 мс | 10 запросов | | Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `bids` — array[object] **обязательный**
  - `advert_id` — integer **обязательный**. ID кампании
  - `nm_id` — integer **обязательный**. Артикул WB
  - `norm_query` — string **обязательный**. Поисковый кластер

## Ответы

**200** — Успешно

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
