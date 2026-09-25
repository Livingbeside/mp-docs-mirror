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
deprecated: true
content_sha: 374da9498ce2c124
---

# Получить отчёт

`GET /api/v1/analytics/goods-return`

> ⚠️ Метод помечен как **deprecated**.

Описание метода

Метод будет отключен [26 октября](/release-notes?id=577).

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
