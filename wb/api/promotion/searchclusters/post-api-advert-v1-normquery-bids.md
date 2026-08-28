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
content_sha: eb65e9a9c7c05f71
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
  - `bidMinorUnits` — integer **обязательный**. Ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances). Допустимый шаг ставки указан в ответе метода [GET /api/advert/v1/config](./promotion#tag/campaignManagement/operation/getV1Config)
  - `nmId` — integer **обязательный**. Артикул WB
  - `normQuery` — string **обязательный**. Поисковый кластер

## Ответы

**200** — Успешно

- `failed` — array[object] **обязательный**
  - `advertId` — integer **обязательный**. ID кампании
  - `nmId` — integer **обязательный**. Артикул WB
  - `normQuery` — string **обязательный**. Поисковый кластер — это группа похожих поисковых запросов, по которым покупатели находят товары
  - `reason` — string **обязательный**. Описание причины ошибки
- `success` — array[object] **обязательный**
  - `advertId` — integer **обязательный**. ID кампании
  - `currency` — string<ISO 4217> **обязательный**. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `nmId` — integer **обязательный**. Артикул WB
  - `normQuery` — string **обязательный**. Поисковый кластер — это группа похожих поисковых запросов, по которым покупатели находят товары

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
