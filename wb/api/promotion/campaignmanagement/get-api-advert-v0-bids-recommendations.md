---
title: Рекомендуемые ставки для карточек товаров и поисковых кластеров{{ /api/advert/v0/bids/recommendations }}
api: wb-promotion
method: GET
path: /api/advert/v0/bids/recommendations
operation_id: getV0BidsRecommendations
tags:
  - campaignManagement
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 1e7eb54ad37a57d2
---

# Рекомендуемые ставки для карточек товаров и поисковых кластеров{{ /api/advert/v0/bids/recommendations }}

`GET /api/advert/v0/bids/recommendations`

Описание метода Метод возвращает рекомендуемые ставки для карточек товаров и поисковых кластеров кампании. Можно использовать для кампаний с типами оплаты `cpm` — за показы и `cpc` — за клики. Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 5 запросов | 12 сек | 5 запросов | | Сервисный | 1 мин | 5 запросов | 12 сек | 5 запросов | | Базовый с секретом | 1 мин | 5 запросов | 12 сек | 5 запросов | | Базовый | 1 ч | 20 запросов | 3 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `nmId` | query | integer<int64> | да | Артикул WB |
| `advertId` | query | integer<int64> | да | ID кампании |

## Ответы

**200** — Успешно

- `advertId` — integer<int64>. ID кампании
- `base` — object. Рекомендуемые ставки для карточек товаров
  - `competitiveBid` — object. Конкурентная ставка — расчётная средняя ставка других продавцов, продающих аналогичные товары по похожей цене. У половины продавцов из расчёта ставка выше конкурентной, а другой половины — ниже
    - `bidKopecks` — integer. Рекомендуемая ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `leadersBid` — object. Лидерская ставка — средняя ставка с которой товары занимают лидирующие позиции в вашей категории товаров
    - `bidKopecks` — integer. Рекомендуемая ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `top2` — object. Топ-ставка
    - `bidKopecks` — integer. Рекомендуемая ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances). Если `0`, для данного предмета топ-ставка не используется
- `nmId` — integer<int64>. Артикул WB
- `normQueries` — array[object]. Рекомендуемые ставки для поисковых кластеров
  - `normQuery` — string. Поисковый кластер
  - `reachMax` — object. Максимальный охват: 76-100%
    - `bidKopecks` — integer. Рекомендуемая ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances).
    - `bidKopecksMin` — integer. Минимальная ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances).
  - `reachMedium` — object. Средний охват: 61-75%
    - `bidKopecks` — integer. Рекомендуемая ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
    - `bidKopecksMin` — integer. Минимальная ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `reachMin` — object. Минимальный охват: 50-60%
    - `bidKopecks` — integer. Рекомендуемая ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
    - `bidKopecksMin` — integer. Минимальная ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `paymentType` — string (cpm). Тип оплаты: - `cpm` — за показы
- `advertId` — integer<int64>. ID кампании
- `levels` — array[object]. Рекомендуемые ставки для карточек товаров
  - `range1To2` — object **обязательный**. Ставка для попадания в позиции 1-2
    - `bidKopecks` — integer. Рекомендуемая ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances).
  - `range3To10` — object **обязательный**. Ставка для попадания в позиции 3-10
    - `bidKopecks` — integer. Рекомендуемая ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances).
  - `range11To34` — object **обязательный**. Ставка для попадания в позиции 11-34
    - `bidKopecks` — integer. Рекомендуемая ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances).
- `nmId` — integer<int64>. Артикул WB
- `paymentType` — string (cpc). Тип оплаты: - `cpc` — за клики

**400** — Неправильный запрос

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
