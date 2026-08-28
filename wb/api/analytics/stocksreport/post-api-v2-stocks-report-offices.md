---
title: Данные по складам{{ /api/v2/stocks-report/offices }}
api: wb-analytics
method: POST
path: /api/v2/stocks-report/offices
operation_id: postV2StocksReportOffices
tags:
  - stocksReport
spec_version: analytics
source: "https://dev.wildberries.ru/docs/openapi/analytics"
deprecated: false
content_sha: 6c7e3c53522d3514
---

# Данные по складам{{ /api/v2/stocks-report/offices }}

`POST /api/v2/stocks-report/offices`

Описание метода Метод формирует набор данных об остатках по складам. Данные по складам продавца приходят в агрегированном виде — по всем сразу, без детализации по конкретным складам — эти записи будут с `"regionName":"Маркетплейс"` и `"offices":[]`. Данные отчёта обновляются 1 раз в час. Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 3 запроса | 20 сек | 3 запроса | | Сервисный | 1 мин | 3 запроса | 20 сек | 3 запроса | | Базовый с секретом | 1 мин | 3 запроса | 20 сек | 3 запроса | | Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `nmIDs` — array[integer<int64>]. Список артикулов WB для фильтрации
- `subjectIDs` — array[integer<int32>]. Список ID предметов для фильтрации
- `brandNames` — array[string]. Список брендов для фильтрации
- `tagIDs` — array[integer<int64>]. Список ID ярлыков для фильтрации
- `currentPeriod` — object **обязательный**. Период
  - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 3 месяцев от текущей даты
  - `end` — string<date> **обязательный**. Дата окончания периода. Не ранее 3 месяцев от текущей даты
- `stockType` — string (, wb, mp) **обязательный**. Тип складов хранения товаров: - `""` — все - `wb` — склады WB - `mp` — склады продавца
- `skipDeletedNm` — boolean **обязательный**. Скрыть удалённые товары

## Ответы

**200** — Успешно

- `data` — object **обязательный**
  - `regions` — array[object]. Множество данных по регионам отгрузки
    - `regionName` — string **обязательный**. Регион отгрузки. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) для складов WB может быть только `Склад WB`
    - `metrics` — object **обязательный**. Метрики по региону
      - `stockCount` — integer<uint64> **обязательный**. Остатки на текущий день, шт.
      - `stockSum` — integer<uint64> **обязательный**. Остатки на текущий день, сумма
      - `saleRate` — object **обязательный**. Оборачиваемость текущих остатков. Особые случаи: 1. `"hours":-1` — бесконечная длительность 2. `"hours":-2` — нулевая длительность 3. `"hours":-3` — нерассчитанная длительность
        - `days` — integer<int32> **обязательный**. Количество дней
        - `hours` — integer<int32> **обязательный**. Количество часов
      - `toClientCount` — integer<uint64> **обязательный**. В пути к клиенту, шт.
      - `fromClientCount` — integer<uint64> **обязательный**. В пути от клиента, шт.
    - `offices` — array[object] **обязательный**. Данные по складам. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `[]`
      - `officeID` — integer<int64> **обязательный**. ID склада
      - `officeName` — string **обязательный**. Название склада
      - `metrics` — object **обязательный**. Метрики по складу
        - `stockCount` — integer<uint64> **обязательный**. Остатки на текущий день, шт.
        - `stockSum` — integer<uint64> **обязательный**. Остатки на текущий день, сумма
        - `saleRate` — object **обязательный**. Оборачиваемость текущих остатков. Особые случаи: 1. `"hours":-1` — бесконечная длительность 2. `"hours":-2` — нулевая длительность 3. `"hours":-3` — нерассчитанная длительность
          - `days` — integer<int32> **обязательный**. Количество дней
          - `hours` — integer<int32> **обязательный**. Количество часов
        - `toClientCount` — integer<uint64> **обязательный**. В пути к клиенту, шт.
        - `fromClientCount` — integer<uint64> **обязательный**. В пути от клиента, шт.
  - `currency` — string **обязательный**. Валюта отчёта

**400** — Неправильный запрос

- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string **обязательный**. Детали ошибки
- `requestId` — string **обязательный**. Уникальный ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**402** — Требуется платёж

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)

**403** — Доступ запрещён

- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string **обязательный**. Детали ошибки
- `requestId` — string **обязательный**. Уникальный ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
