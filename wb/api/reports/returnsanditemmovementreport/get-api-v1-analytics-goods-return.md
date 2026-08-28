---
title: Получить отчёт
api: wb-reports
method: GET
path: /api/v1/analytics/goods-return
operation_id: getV1AnalyticsGoodsReturn
tags:
  - returnsAndItemMovementReport
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 36163b50e65f3e3f
---

# Получить отчёт

`GET /api/v1/analytics/goods-return`

Описание метода

Метод возвращает отчёт о [возвратах товаров продавцу](https://seller.wildberries.ru/analytics-reports/goods-return). 

Можно получить отчёт максимум за 31 день.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 1 запрос | 1 мин | 10 запросов |
| Сервисный | 1 мин | 1 запрос | 1 мин | 10 запросов |
| Базовый с секретом | 1 мин | 1 запрос | 1 мин | 10 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `dateFrom` | query | string<date> | да | Дата начала отчётного периода |
| `dateTo` | query | string<date> | да | Дата окончания отчётного периода |

## Ответы

**200** — Успешно

- `report` — array[object]. Отчёт
  - `barcode` — string. Баркод
  - `brand` — string. Бренд
  - `completedDt` — string. Дата и время выдачи возврата продавцу
  - `dstOfficeAddress` — string. Адрес ПВЗ выдачи возврата
  - `dstOfficeId` — integer. ID ПВЗ выдачи возврата
  - `expiredDt` — string. Дата и время истечения срока хранения возврата
  - `isStatusActive` — integer (0, 1). Тип статуса возврата: * `0` — архивный * `1` — активный
  - `nmId` — integer. Артикул WB
  - `orderDt` — string<date>. Дата заказа на возврат
  - `orderId` — integer. Номер сборочного задания
  - `readyToReturnDt` — string. Дата и время готовности возврата к выдаче
  - `reason` — string. Причина возврата
  - `returnType` — string. Тип возврата
  - `shkId` — integer. Штрихкод
  - `srid` — string. Уникальный ID заказа на возврат
  - `status` — string. Статус возврата
  - `stickerId` — string. Стикер заказа на возврат
  - `subjectName` — string. Предмет
  - `techSize` — string. Размер

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
