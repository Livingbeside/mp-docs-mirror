---
title: Получить отчёт
api: wb-reports
method: GET
path: /api/analytics/v1/item-returns
operation_id: getAnalyticsV1GoodsReturn
tags:
  - returnsAndItemMovementReport
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: d76696162222c90f
---

# Получить отчёт

`GET /api/analytics/v1/item-returns`

Описание метода

Метод возвращает отчёт о [возвратах товаров продавцу](https://seller.wildberries.ru/return-transfer-reports).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `dateFrom` | query | string<date> | да | Дата начала отчётного периода |
| `dateTo` | query | string<date> | да | Дата окончания отчётного периода |
| `status` | query | string (active, archive) | да | Статус возврата: - `archive` — архивный - `active` — активный |
| `limit` | query | integer<date> | да | Количество возвратов в ответе |
| `offset` | query | integer<date> | да | Сколько элементов пропустить. Например, для значения 10 ответ начнется с 11 элемента |

## Ответы

**200** — Успешно

- `count` — integer **обязательный**. Общее количество возвратов за запрашиваемый период
- `report` — array[object] **обязательный**. Отчёт
  - `sku` — string **обязательный**. Баркод
  - `brand` — string **обязательный**. Бренд
  - `completedDt` — string **обязательный**. Дата и время выдачи возврата продавцу
  - `dstOfficeAddress` — string **обязательный**. Адрес ПВЗ для выдачи возврата продавцу
  - `kiz` — string **обязательный**. Код маркировки [Честного знака](https://честныйзнак.рф/)
  - `dstOfficeId` — integer **обязательный**. ID ПВЗ для выдачи возврата продавцу
  - `expiredDt` — string **обязательный**. Дата и время истечения срока хранения возврата
  - `nmId` — integer **обязательный**. Артикул WB
  - `orderDt` — string<date> **обязательный**. Дата заказа на возврат
  - `orderId` — integer **обязательный**. ID сборочного задания
  - `readyToReturnDt` — string **обязательный**. Дата и время готовности возврата к выдаче
  - `returnReason` — string. Причина возврата. Поле возвращается только при `"returnType":"Возврат неопознанного товара"`
  - `returnType` — string **обязательный**. Тип возврата
  - `shkId` — integer **обязательный**. Штрихкод
  - `srid` — string **обязательный**. ID заказа на возврат
  - `returnStatus` — string **обязательный**. Статус возврата
  - `stickerId` — string **обязательный**. Стикер заказа на возврат
  - `subjectName` — string **обязательный**. Предмет
  - `techSize` — string **обязательный**. Размер

**204** — Нет данных

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
