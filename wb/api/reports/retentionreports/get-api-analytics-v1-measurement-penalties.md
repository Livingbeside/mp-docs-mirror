---
title: Удержания за занижение габаритов упаковки
api: wb-reports
method: GET
path: /api/analytics/v1/measurement-penalties
operation_id: getV1MeasurementPenalties
tags:
  - retentionReports
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 862822abeeca3322
---

# Удержания за занижение габаритов упаковки

`GET /api/analytics/v1/measurement-penalties`

Описание метода

Метод возвращает отчёт об [удержаниях за занижение габаритов упаковки](https://seller.wildberries.ru/analytics-reports/dimensions-penalties)

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
| `limit` | query | integer | да | Количество удержаний в ответе |
| `offset` | query | integer | нет | Сколько элементов пропустить. Например, для значения `10` ответ начнётся с 11 элемента |

## Ответы

**200** — Успешно

- `data` — object **обязательный**. Данные ответа
  - `reports` — array[object] **обязательный**. Удержания
    - `dimId` — integer. ID замера
    - `dtBonus` — string<date-time>. Дата штрафа
    - `height` — integer. Высота, см (фактические габариты по замеру на складе)
    - `heightSup` — integer. Высота, см (габариты карточки товара)
    - `isValid` — boolean. Статус обмера: - `false` — отменён - `true` — подтверждён
    - `isValidDt` — string<date-time>. Дата и время подтверждения или отмены обмера
    - `length` — integer. Длина, см (фактические габариты по замеру на складе)
    - `lengthSup` — integer. Длина, см (габариты карточки товара)
    - `nmId` — integer. Артикул WB
    - `penaltyAmount` — number. Сумма штрафа
    - `photoUrls` — array[string]. Фото замеров
    - `prcOver` — number. Разница в габаритах, %
    - `reversalAmount` — number. Сумма сторно
    - `subjectName` — string. Предмет
    - `volume` — number. Объём, л (фактические габариты по замеру на складе)
    - `volumeSup` — number. Объём, л (габариты карточки товара)
    - `width` — integer. Ширина, см (фактические габариты по замеру на складе)
    - `widthSup` — integer. Ширина, см (габариты карточки товара)
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
