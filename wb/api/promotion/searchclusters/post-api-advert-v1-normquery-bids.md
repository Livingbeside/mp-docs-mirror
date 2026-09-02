---
title: Установить ставки для поисковых кластеров в валюте аккаунта продавца
api: wb-promotion
method: POST
path: /api/advert/v1/normquery/bids
operation_id: postV1NormqueryBids
tags:
  - searchClusters
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 116d2d4b3386e97d
---

# Установить ставки для поисковых кластеров в валюте аккаунта продавца

`POST /api/advert/v1/normquery/bids`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену

Метод устанавливает ставки на поисковые кластеры в валюте [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances).
Можно использовать только для кампаний c ручной ставкой и моделью оплаты `cpm` — за показы.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 2 запроса | 500 мс | 4 запроса |
| Сервисный | 1 сек | 2 запроса | 500 мс | 4 запроса |

## Запрос

**Тело запроса** (`application/json`):

- `bids` — array[object] **обязательный**
  - `advertId` — integer **обязательный**. ID кампании
  - `nmId` — integer **обязательный**. Артикул WB
  - `normQuery` — string **обязательный**. Поисковый кластер
  - `bidMinorUnits` — integer **обязательный**. Ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances). Допустимый шаг ставки указан в ответе метода [GET /api/advert/v1/config](./promotion#tag/campaignManagement/operation/getV1Config)

## Ответы

**200** — Успешно

- `success` — array[object] **обязательный**
  - `advertId` — integer **обязательный**. ID кампании
  - `nmId` — integer **обязательный**. Артикул WB
  - `normQuery` — string **обязательный**. Поисковый кластер — это группа похожих поисковых запросов, по которым покупатели находят товары
  - `currency` — string<ISO 4217> **обязательный**. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `failed` — array[object] **обязательный**
  - `advertId` — integer **обязательный**. ID кампании
  - `nmId` — integer **обязательный**. Артикул WB
  - `normQuery` — string **обязательный**. Поисковый кластер — это группа похожих поисковых запросов, по которым покупатели находят товары
  - `reason` — string **обязательный**. Описание причины ошибки

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
