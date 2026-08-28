---
title: Получить предметы, которые не хранятся на складах WB
api: wb-orders-fbs
method: GET
path: /api/marketplace/v3/fbs/settings/autoreturns/subcategories/restricted
operation_id: getMarketplaceV3FbsSettingsAutoreturnsSubcategoriesRestricted
tags:
  - autoreturnSettings
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 21d8883a6e875806
---

# Получить предметы, которые не хранятся на складах WB

`GET /api/marketplace/v3/fbs/settings/autoreturns/subcategories/restricted`

Описание метода

 Метод доступен по
 Персональному токену

Метод возвращает список ID предметов, товары которых не могут храниться на складах WB и будут возвращены в ПВЗ автоматически.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `next` | query | integer<int64> | да | Параметр пагинации. Устанавливает значение, с которого надо получить следующий пакет данных. Для получения полного списка данных должен быть равен `0` в первом запросе. Для следующих запросов необходимо брать значения из одноимённого поля в ответе. |
| `limit` | query | integer<int32> | да | Количество предметов в ответе |

## Ответы

**200** — Успешно

- `data` — array[object] **обязательный**. Список ID предметов, товары которых не хранятся на складах WB
  - `subjectId` — integer **обязательный**. ID предмета
- `next` — integer<int64> **обязательный**. Параметр пагинации. Содержит значение, которое необходимо указать в запросе для получения следующего пакета данных

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
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
