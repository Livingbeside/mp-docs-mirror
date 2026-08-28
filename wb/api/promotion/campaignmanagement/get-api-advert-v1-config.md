---
title: Конфигурационные значения продвижения
api: wb-promotion
method: GET
path: /api/advert/v1/config
operation_id: getV1Config
tags:
  - campaignManagement
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 7f0afce1114bf56a
---

# Конфигурационные значения продвижения

`GET /api/advert/v1/config`

Описание метода

Метод возвращает валюту, код валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances) и допустимые шаги ставок для метода [POST /api/advert/v1/normquery/bids](./promotion#tag/searchClusters/operation/postV1NormqueryBids)

 Метод доступен по
 Персональному токену, 
 Сервисному токену

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1 запрос | 1 мин | 10 запросов |

## Ответы

**200** — Успешно

- `cpcStep` — integer<int64> **обязательный**. Шаг ставки в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances) для кампаний CPC
- `cpmStep` — integer<int64> **обязательный**. Шаг ставки в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances) для CPM-кампаний
- `currency` — string<ISO 4217> **обязательный**. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `currencyCode` — integer **обязательный**. Код валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `minTopUp` — integer<int64> **обязательный**. Минимальная сумма пополнения бюджета кампании в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances). Например, минимальная сумма пополнения бюджета при `"minTopUp": 10000` и `"currency": "UZS"` — 100 узбекских сум

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
