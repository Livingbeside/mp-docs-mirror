---
title: Заказы и позиции по поисковым запросам товара{{ /api/v2/search-report/product/orders }}
api: wb-analytics
method: POST
path: /api/v2/search-report/product/orders
operation_id: postV2SearchReportProductOrders
tags:
  - searchQueriesForYourItems
spec_version: analytics
source: "https://dev.wildberries.ru/docs/openapi/analytics"
deprecated: false
content_sha: 500107a6061e2097
---

# Заказы и позиции по поисковым запросам товара{{ /api/v2/search-report/product/orders }}

`POST /api/v2/search-report/product/orders`

Описание метода Метод формирует данные для таблицы: - о заказах по каждому поисковому запросу для конкретного товара - о позициях товара в результатах поиска по каждому запросу Данные указаны в рамках периода для [запрошенного товара](./analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportProductSearchTexts) и сгруппированы по дням. Максимальный период — 7 дней. Данные отчёта обновляются 1 раз в час. Можно получить отчёт максимум за последние 365 дней с момента выполнения запроса Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 3 запроса | 20 сек | 3 запроса | | Сервисный | 1 мин | 3 запроса | 20 сек | 3 запроса | | Базовый с секретом | 1 мин | 3 запроса | 20 сек | 3 запроса | | Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `period` — object **обязательный**. Текущий период. Максимум 7 суток
  - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 365 суток от сегодня
  - `end` — string<date> **обязательный**. Дата окончания периода. Не ранее 365 суток от сегодня
- `nmId` — integer<uint64> **обязательный**. Артикул WB
- `searchTexts` — array[string] **обязательный**. Поисковые запросы. Для тарифов [Джема](https://seller.wildberries.ru/monetization/tariffs) **Продвинутый** и **Премиальный** максимум — 100

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
- `data` — object **обязательный**
  - `total` — array[object] **обязательный**. Итог по товарам
    - `dt` — string<date> **обязательный**. Дата сбора статистики
    - `avgPosition` — integer<uint64> **обязательный**. Средняя позиция товара в результатах поиска
    - `orders` — integer<uint64> **обязательный**. Сколько раз товары из поиска заказали
  - `items` — array[object] **обязательный**. Элементы таблицы
    - `text` — string **обязательный**. Текст поискового запроса
    - `frequency` — integer<uint64> **обязательный**. Количество обращений с поисковым запросом
    - `dateItems` — array[object] **обязательный**. Статистика по датам
      - `dt` — string<date> **обязательный**. Дата сбора статистики
      - `avgPosition` — integer<uint64> **обязательный**. Средняя позиция товара в результатах поиска
      - `orders` — integer<uint64> **обязательный**. Сколько раз товары из поиска заказали

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
