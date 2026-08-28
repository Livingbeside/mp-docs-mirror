---
title: Удержания за занижение габаритов упаковки{{ /api/analytics/v1/measurement-penalties }}
api: wb-reports
method: GET
path: /api/analytics/v1/measurement-penalties
operation_id: getV1MeasurementPenalties
tags:
  - retentionReports
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 7ba207e74b6614fb
---

# Удержания за занижение габаритов упаковки{{ /api/analytics/v1/measurement-penalties }}

`GET /api/analytics/v1/measurement-penalties`

Описание метода Метод возвращает отчёт об [удержаниях за занижение габаритов упаковки](https://seller.wildberries.ru/analytics-reports/dimensions-penalties) Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 1 запрос | 1 мин | 1 запрос | | Сервисный | 1 мин | 1 запрос | 1 мин | 1 запрос | | Базовый с секретом | 1 мин | 1 запрос | 1 мин | 1 запрос | | Базовый | 6 ч | 1 запрос | 6 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `dateFrom` | query | string<date-time> | нет | Начало отчётного периода. По умолчанию используется дата, когда были впервые получены данные для отчёта |
| `dateTo` | query | string<date-time> | да | Конец отчётного периода |
| `limit` | query | integer | да | Количество удержаний в ответе |
| `offset` | query | integer | нет | Сколько элементов пропустить. Например, для значения `10` ответ начнётся с 11 элемента |

## Ответы

**200** — Успешно

- `data` — object **обязательный**. Данные ответа
  - `reports` — array[object] **обязательный**. Удержания
    - `nmId` — integer. Артикул WB
    - `subjectName` — string. Предмет
    - `dimId` — integer. ID замера
    - `prcOver` — number. Разница в габаритах, %
    - `volume` — number. Объём, л (фактические габариты по замеру на складе)
    - `width` — integer. Ширина, см (фактические габариты по замеру на складе)
    - `length` — integer. Длина, см (фактические габариты по замеру на складе)
    - `height` — integer. Высота, см (фактические габариты по замеру на складе)
    - `volumeSup` — number. Объём, л (габариты карточки товара)
    - `widthSup` — integer. Ширина, см (габариты карточки товара)
    - `lengthSup` — integer. Длина, см (габариты карточки товара)
    - `heightSup` — integer. Высота, см (габариты карточки товара)
    - `photoUrls` — array[string]. Фото замеров
    - `dtBonus` — string<date-time>. Дата штрафа
    - `isValid` — boolean. Статус обмера: - `false` — отменён - `true` — подтверждён
    - `isValidDt` — string<date-time>. Дата и время подтверждения или отмены обмера
    - `reversalAmount` — number. Сумма сторно
    - `penaltyAmount` — number. Сумма штрафа
  - `total` — integer **обязательный**. Количество удержаний в отчёте. Без учёта `limit` и `offset`

**400** — Неправильный запрос

- `title` — string. Заголовок ошибки
- `status` — integer. HTTP статус-код
- `detail` — string. Детали ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB

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

- `title` — string. Заголовок ошибки
- `status` — integer. HTTP статус-код
- `detail` — string. Детали ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
