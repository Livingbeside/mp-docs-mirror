---
title: Остатки на складах WB
api: wb-analytics
method: POST
path: /api/analytics/v1/stocks-report/wb-warehouses
operation_id: postV1StocksReportWbWarehouses
tags:
  - stocksReport
spec_version: analytics
source: "https://dev.wildberries.ru/docs/openapi/analytics"
deprecated: false
content_sha: 7a466244c9694865
---

# Остатки на складах WB

`POST /api/analytics/v1/stocks-report/wb-warehouses`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену, 
 Базовому токену с секретом

Метод возвращает текущие остатки товаров на складах WB.

Данные обновляются 1 раз в 30 минут.

1 строка ответа — данные об 1 размере товара на 1 складе WB.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 3 запроса | 20 сек | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `nmIds` — array[integer<int64>]. Артикулы WB
- `chrtIds` — array[integer<uint64>]. ID размеров. Используется только для указанных в массиве `nmIds` артикулов
- `limit` — integer<uint32>. Количество строк в ответе По умолчанию: `250000`.
- `offset` — integer<uint32>. Сколько элементов пропустить. Например, для значения `10` ответ начнётся с 11 элемента По умолчанию: `0`.

## Ответы

**200** — Успешно

- `data` — object **обязательный**. Текущие остатки товаров на складах WB
  - `items` — array[object] **обязательный**. Остатки товаров на складах WB по размерам
    - `nmId` — integer<int64> **обязательный**. Артикул WB
    - `chrtId` — integer<uint64> **обязательный**. ID размера
    - `warehouseId` — integer<int64> **обязательный**. ID склада. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `-999999`
    - `warehouseName` — string **обязательный**. Название склада. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `Склад WB`
    - `regionName` — string **обязательный**. Регион отгрузки. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `Склад WB`
    - `quantity` — integer<uint64> **обязательный**. Количество товара на складе, доступное клиентам для добавления в корзину
    - `inWayToClient` — integer<uint64> **обязательный**. В пути к клиенту
    - `inWayFromClient` — integer<uint64> **обязательный**. В пути от клиента

**204** — Нет данных

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
