---
title: Конфигурационные значения продвижения{{ /api/advert/v1/config }}
api: wb-promotion
method: GET
path: /api/advert/v1/config
operation_id: getV1Config
tags:
  - campaignManagement
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 495ed5bed4af8a15
---

# Конфигурационные значения продвижения{{ /api/advert/v1/config }}

`GET /api/advert/v1/config`

Описание метода Метод возвращает валюту, код валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances) и допустимые шаги ставок для метода [POST /api/advert/v1/normquery/bids](./promotion#tag/searchClusters/operation/postV1NormqueryBids) Метод доступен по Персональному токену, Сервисному токену Лимит запросов на один аккаунт продавца: | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 1 запрос | 1 мин | 10 запросов |

## Ответы

**200** — Успешно

- `currency` — string<ISO 4217> **обязательный**. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `currencyCode` — integer **обязательный**. Код валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `cpmStep` — integer<int64> **обязательный**. Шаг ставки в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances) для CPM-кампаний
- `cpcStep` — integer<int64> **обязательный**. Шаг ставки в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances) для кампаний CPC
- `minTopUp` — integer<int64> **обязательный**. Минимальная сумма пополнения бюджета кампании в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances). Например, минимальная сумма пополнения бюджета при `"minTopUp": 10000` и `"currency": "UZS"` — 100 узбекских сум

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
