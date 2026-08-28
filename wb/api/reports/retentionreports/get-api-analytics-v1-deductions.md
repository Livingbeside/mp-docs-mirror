---
title: Подмены и неверные вложения
api: wb-reports
method: GET
path: /api/analytics/v1/deductions
operation_id: getV1Deductions
tags:
  - retentionReports
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: e97755ba45763b7e
---

# Подмены и неверные вложения

`GET /api/analytics/v1/deductions`

Описание метода

Метод возвращает отчёт об удержаниях за [подмены и неверные вложения](https://seller.wildberries.ru/analytics-reports/dimensions-penalties/retentions)

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Сервисный | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Базовый с секретом | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `dateFrom` | query | string<date-time> | нет | Начало отчётного периода. По умолчанию используются дата и время, когда были впервые получены данные для отчёта |
| `dateTo` | query | string<date-time> | да | Конец отчётного периода |
| `sort` | query | string (nmId, dtBonus, bonusSumm) | нет | Сортировка: - `nmId` — по артикулу WB - `dtBonus` — по дате и времени удержания - `bonusSumm` — по сумме удержания |
| `order` | query | string (desc, asc) | нет | Порядок выдачи: - `desc` — по убыванию - `asc` — по возрастанию |
| `limit` | query | integer | да | Количество удержаний в ответе |
| `offset` | query | integer | нет | Сколько элементов пропустить. Например, для значения `10` ответ начнётся с 11 элемента |

## Ответы

**200** — Успешно

- `data` — object **обязательный**. Данные ответа
  - `reports` — array[object] **обязательный**. Удержания
    - `bonusSumm` — number. Сумма удержания
    - `bonusType` — string. Причина удержания
    - `dtBonus` — string<date-time>. Дата и время удержания
    - `newColor` — string. Новый цвет
    - `newShkId` — integer. Новый штрихкод
    - `newSize` — string. Новый размер
    - `newSku` — string. Новый баркод
    - `newVendorCode` — string. Новый артикул продавца
    - `nmId` — integer. Артикул WB
    - `oldColor` — string. Старый цвет
    - `oldShkId` — integer. Старый штрихкод
    - `oldSize` — string. Старый размер
    - `oldSku` — string. Старый баркод
    - `oldVendorCode` — string. Старый артикул продавца
    - `photoUrls` — array[string]. Фото замеров
  - `total` — integer **обязательный**. Количество удержаний в отчёте. Без учёта `limit` и `offset`

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
