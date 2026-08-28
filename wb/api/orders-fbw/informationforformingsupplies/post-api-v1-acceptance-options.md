---
title: Опции приёмки
api: wb-orders-fbw
method: POST
path: /api/v1/acceptance/options
operation_id: postV1AcceptanceOptions
tags:
  - informationForFormingSupplies
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: 1cf703d01d8088da
---

# Опции приёмки

`POST /api/v1/acceptance/options`

Описание метода

Метод [временно отключён](https://dev.wildberries.ru/release-notes?id=570)

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 6 запросов | 10 сек | 6 запросов |
| Сервисный | 1 мин | 6 запросов | 10 сек | 6 запросов |
| Базовый с секретом | 1 мин | 6 запросов | 10 сек | 6 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `warehouseID` | query | integer | нет | ID склада. Если параметр не указан, возвращаются данные по всем складам. **Максимум одно значение** |

## Запрос

**Тело запроса** (`application/json`):

- `quantity` — integer. Суммарное количество товаров, планируемых для поставки. **Максимум 999999**
- `barcode` — string. Баркод из карточки товара

## Ответы

**200** — Успешно

- `result` — array[object]
  - `barcode` — string. Баркод из карточки товара
  - `error` — object. Данные ошибки. При наличии
    - `title` — string. ID ошибки
    - `detail` — string. Описание ошибки
  - `isError` — boolean. Наличие ошибки: - `true` — ошибка есть - Поля нет — ошибка отсутствует
  - `warehouses` — array[object]. Список складов. При наличии ошибки будет `null`
    - `warehouseID` — integer. ID склада. По нему можно получить [информацию о складе](./orders-fbw#tag/informationForFormingSupplies/operation/getV1Warehouses)
    - `canBox` — boolean. Тип упаковки **Короб**: - `true` — доступен - `false` — недоступен
    - `canMonopallet` — boolean. Тип упаковки **Монопаллета**: - `true` — доступен - `false` — недоступен
    - `canSupersafe` — boolean. Тип упаковки **Суперсейф**: - `true` — доступен - `false` — недоступен
    - `isBoxOnPallet` — boolean. Тип поставки **Поштучная палета**: - `true` — доступен - `false` — недоступен
- `requestId` — string. ID запроса при наличии ошибок

**400** — Некорректный запрос

- `status` — integer. HTTP статус-код
- `title` — string. ID ошибки
- `detail` — string. Описание ошибки
- `requestId` — string. ID запроса
- `origin` — string. Сервис, вернувший ошибку

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

**404** — Не найдено

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
