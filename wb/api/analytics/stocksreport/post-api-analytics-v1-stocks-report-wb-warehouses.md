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
content_sha: 4224000a3dd4124d
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

- `chrtIds` — array[integer<int64>]. ID размеров. Используется только для указанных в массиве `nmIds` артикулов
- `limit` — integer<uint32>. Количество строк в ответе По умолчанию: `250000`.
- `nmIds` — array[integer<int64>]. Артикулы WB
- `offset` — integer<uint32>. Сколько элементов пропустить. Например, для значения `10` ответ начнётся с 11 элемента По умолчанию: `0`.

## Ответы

**200** — Успешно

- `data` — object **обязательный**. Текущие остатки товаров на складах WB
  - `items` — array[object] **обязательный**. Остатки товаров на складах WB по размерам
    - `chrtId` — integer<int64> **обязательный**. ID размера
    - `inWayFromClient` — integer<uint64> **обязательный**. В пути от клиента
    - `inWayToClient` — integer<uint64> **обязательный**. В пути к клиенту
    - `nmId` — integer<int64> **обязательный**. Артикул WB
    - `quantity` — integer<uint64> **обязательный**. Количество товара на складе, доступное клиентам для добавления в корзину
    - `regionName` — string **обязательный**. Регион отгрузки. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `Склад WB`
    - `warehouseId` — integer<int64> **обязательный**. ID склада. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `-999999`
    - `warehouseName` — string **обязательный**. Название склада. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `Склад WB`

**204** — Нет данных

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

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

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
