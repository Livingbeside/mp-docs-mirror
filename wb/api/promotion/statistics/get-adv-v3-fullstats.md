---
title: Статистика кампаний
api: wb-promotion
method: GET
path: /adv/v3/fullstats
operation_id: getV3Fullstats
tags:
  - statistics
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 4192ede9490dc086
---

# Статистика кампаний

`GET /adv/v3/fullstats`

Описание метода

Метод формирует статистику для кампаний независимо от типа.

Максимальный период в запросе — 31 день.

Для кампаний в статусах `7`, `9` и `11`.

В песочнице статистика кампаний доступна за последние 30 дней. Генерируется только для компаний в статусе `9`, тип `8`, 9 раз в сутки

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 3 запроса | 20 сек | 1 запрос |
| Сервисный | 1 мин | 3 запроса | 20 сек | 1 запрос |
| Базовый с секретом | 1 мин | 3 запроса | 20 сек | 1 запрос |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `ids` | query | string | да | ID кампаний, максимум 50 значений |
| `beginDate` | query | string<date> | да | Дата начала интервала |
| `endDate` | query | string<date> | да | Дата окончания интервала |

## Ответы

**200** — Успешно

- `advertId` — integer **обязательный**. ID кампании
- `atbs` — integer **обязательный**. Количество добавлений товаров в корзину
- `boosterStats` — array[object]
  - `avg_position` — integer **обязательный**. Средняя позиция товара
  - `date` — string<date> **обязательный**. Дата, за которую предоставлены данные
  - `nm` — integer **обязательный**. Артикул WB
- `canceled` — integer **обязательный**. Отмены, шт.
- `clicks` — integer **обязательный**. Количество кликов
- `cpc` — number<double> **обязательный**. Средняя стоимость клика в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `cr` — number<double> **обязательный**. CR (conversion rate) — отношение количества заказов к общему количеству кликов
- `ctr` — number<double> **обязательный**. CTR (click-through rate) — отношение числа кликов к количеству показов в процентах
- `days` — array[object] **обязательный**
  - `apps` — array[object] **обязательный**. Блок информации о платформе
    - `appType` — integer (1, 32, 64) **обязательный**. Тип платформы: - `1` — сайт - `32` — Android - `64` — IOS
    - `atbs` — integer **обязательный**. Количество добавлений товаров в корзину
    - `canceled` — integer **обязательный**. Отмены, шт.
    - `clicks` — integer **обязательный**. Количество кликов
    - `cpc` — number **обязательный**. Средняя стоимость клика в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
    - `cr` — number **обязательный**. CR (conversion rate) — отношение количества заказов к общему количеству кликов
    - `ctr` — number **обязательный**. CTR (click-through rate) — отношение числа кликов к количеству показов в процентах
    - `nms` — array[object] **обязательный**. Блок статистики по артикулам WB
      - `atbs` — integer **обязательный**. Количество добавлений товаров в корзину
      - `canceled` — integer **обязательный**. Отмены, шт.
      - `clicks` — integer **обязательный**. Количество кликов
      - `cpc` — number **обязательный**. Средняя стоимость клика в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
      - `cr` — number **обязательный**. CR (conversion rate) — отношение количества заказов к общему количеству кликов
      - `ctr` — number **обязательный**. CTR (click-through rate) — отношение числа кликов к количеству показов в процентах
      - `name` — string **обязательный**. Название товара
      - `nmId` — integer **обязательный**. Артикул WB
      - `orders` — integer **обязательный**. Количество заказов
      - `shks` — integer **обязательный**. Количество заказанных товаров, шт.
      - `sum` — number **обязательный**. Затраты в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
      - `sum_price` — number **обязательный**. Заказов на сумму в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
      - `views` — integer **обязательный**. Количество просмотров
    - `orders` — integer **обязательный**. Количество заказов
    - `shks` — integer **обязательный**. Количество заказанных товаров, шт.
    - `sum` — number **обязательный**. Затраты в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
    - `sum_price` — number **обязательный**. Заказов на сумму в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
    - `views` — integer **обязательный**. Количество просмотров
  - `atbs` — integer **обязательный**. Количество добавлений товаров в корзину
  - `canceled` — integer **обязательный**. Отмены, шт.
  - `date` — string<date-time> **обязательный**. Дата, за которую представлены данные
  - `clicks` — integer **обязательный**. Количество кликов
  - `cpc` — number **обязательный**. Средняя стоимость клика в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `cr` — number **обязательный**. CR (conversion rate) — отношение количества заказов к общему количеству посещений кампании
  - `ctr` — number **обязательный**. CTR (click-through rate) — отношение числа кликов к количеству показов в процентах
  - `orders` — integer **обязательный**. Количество заказов
  - `shks` — integer **обязательный**. Количество заказанных товаров, шт.
  - `sum` — number **обязательный**. Затраты в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `sum_price` — number **обязательный**. Заказов на сумму в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `views` — integer **обязательный**. Количество просмотров
- `orders` — integer **обязательный**. Количество заказов
- `shks` — integer **обязательный**. Количество заказанных товаров, шт.
- `sum` — number<double> **обязательный**. Затраты в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `sum_price` — number<double> **обязательный**. Сумма заказов в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `views` — integer **обязательный**. Количество просмотров
- `currency` — string<ISO 4217> **обязательный**. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)

**400** — Неправильный запрос

- `errors` — array[object]
  - `detail` — string. Детали ошибки
  - `field` — string. Параметр с ошибкой
- `detail` — string. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `request_id` — string **обязательный**. ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки
- `type` — string. Тип ошибки

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
