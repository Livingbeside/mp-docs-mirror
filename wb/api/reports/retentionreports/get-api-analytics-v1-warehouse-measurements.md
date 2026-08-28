---
title: Замеры склада
api: wb-reports
method: GET
path: /api/analytics/v1/warehouse-measurements
operation_id: getV1WarehouseMeasurements
tags:
  - retentionReports
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 8ef999926ffe7c90
---

# Замеры склада

`GET /api/analytics/v1/warehouse-measurements`

Описание метода

Метод возвращает отчёт о [замерах склада](https://seller.wildberries.ru/analytics-reports/dimensions-penalties/warehouse-measurements)

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Сервисный | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Базовый с секретом | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Базовый | 6 ч | 1 запрос | 6 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `dateFrom` | query | string<date-time> | нет | Начало отчётного периода. По умолчанию используется дата, когда были впервые получены данные для отчёта |
| `dateTo` | query | string<date-time> | да | Конец отчётного периода |
| `limit` | query | integer | да | Количество замеров в ответе |
| `offset` | query | integer | нет | Сколько элементов пропустить. Например, для значения `10` ответ начнётся с 11 элемента |

## Ответы

**200** — Успешно

- `data` — object **обязательный**. Данные ответа
  - `reports` — array[object] **обязательный**. Замеры
    - `dimId` — integer. ID замера
    - `dt` — string<date-time>. Дата и время
    - `height` — integer. Высота, см
    - `length` — integer. Длина, см
    - `nmId` — integer. Артикул WB
    - `photoUrls` — array[string]. Фото замеров
    - `subjectName` — string. Предмет
    - `volume` — number. Объём, л
    - `width` — integer. Ширина, см
  - `total` — integer **обязательный**. Количество замеров в отчёте. Без учёта `limit` и `offset`

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — integer. HTTP статус-код
- `title` — string. Заголовок ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**402** — Требуется платёж

- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)
- `title` — string. Заголовок ошибки

**403** — Доступ запрещён

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — integer. HTTP статус-код
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
