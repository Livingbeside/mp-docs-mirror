---
title: Плоская статистика кампаний
api: wb-promotion
method: GET
path: /api/advert/v4/fullstats
operation_id: getV4Fullstats
tags:
  - statistics
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 5b21dee44edb988a
---

# Плоская статистика кампаний

`GET /api/advert/v4/fullstats`

Описание метода

Метод формирует статистику кампаний в плоском формате (без вложенной иерархии) с разделением по зонам показов и типам конверсии.

Максимальный период в запросе — 31 день.

Для кампаний в статусах `7`, `9` и `11`.

Лимит запросов на один профиль продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 3 запроса | 20 сек | 1 запрос |
| Сервисный | 1 мин | 3 запроса | 20 сек | 1 запрос |
| Базовый с секретом | 1 мин | 3 запроса | 20 сек | 1 запрос |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `advertIds` | query | array[integer<int64>] | да | Список ID рекламных кампаний |
| `beginDate` | query | string<date> | да | Дата начала интервала |
| `endDate` | query | string<date> | да | Дата окончания интервала |

## Ответы

**200** — Успешно

- `rows` — array[object] **обязательный**
  - `advertId` — integer<int64> **обязательный**. ID рекламной кампании
  - `nmId` — integer<int64> **обязательный**. Артикул WB
  - `date` — string<date> **обязательный**. Дата, за которую предоставлены данные
  - `placement` — string (search, recommendation) **обязательный**. Место размещения кампании: - `search` — поиск - `recommendations` — рекомендации
  - `conversionType` — string (direct, multicard, associated) **обязательный**. Тип конверсии: - `direct` — заказ рекламируемого товара. Показы, клики и расход относятся к конверсии этого типа - `multicard` — заказ другого варианта товара из этой карточки - `associated` — заказ другого товара
  - `currency` — string<ISO 4217> **обязательный**. Валюта [профиля продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `views` — integer<int64> **обязательный**. Показы. Для `"conversionType":"multicard"` и `"conversionType":"associated"` возвращается `0`, если показ был на другом товаре
  - `clicks` — integer<int64> **обязательный**. Количество кликов. Только для `"conversionType":"direct"`
  - `ctr` — number<double> **обязательный**. Кликабельность — отношение числа кликов к количеству показов, %
  - `cpc` — number<double> **обязательный**. Стоимость клика в базовых единицах валюты [профиля продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `sum` — number<double> **обязательный**. Затраты в базовых единицах валюты [профиля продавца](https://cmp.wildberries.ru/campaigns/finances). Только для `"conversionType":"direct"`
  - `atbs` — integer **обязательный**. Сколько раз товар добавили в корзину
  - `orders` — integer **обязательный**. Количество заказов
  - `cr` — number<double> **обязательный**. Отношение количества заказов к общему количеству кликов
  - `shks` — integer **обязательный**. Количество заказанных товаров, шт.
  - `sumPrice` — number<double> **обязательный**. Сумма заказов в базовых единицах валюты [профиля продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `canceled` — integer **обязательный**. Количество отмен
  - `avgPos` — number<double>. Средняя позиция товара на страницах поисковой выдачи. Возвращается только при комбинации значений `"placement":search` и `"conversionType":"direct"`

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
