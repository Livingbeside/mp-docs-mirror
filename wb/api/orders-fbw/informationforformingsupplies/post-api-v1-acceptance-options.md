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
content_sha: e81b9f29cc416a01
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

- `barcode` — string. Баркод из карточки товара
- `quantity` — integer. Суммарное количество товаров, планируемых для поставки. **Максимум 999999**

## Ответы

**200** — Успешно

- `requestId` — string. ID запроса при наличии ошибок
- `result` — array[object]
  - `barcode` — string. Баркод из карточки товара
  - `error` — object. Данные ошибки. При наличии
    - `detail` — string. Описание ошибки
    - `title` — string. ID ошибки
  - `isError` — boolean. Наличие ошибки: - `true` — ошибка есть - Поля нет — ошибка отсутствует
  - `warehouses` — array[object]. Список складов. При наличии ошибки будет `null`
    - `canBox` — boolean. Тип упаковки **Короб**: - `true` — доступен - `false` — недоступен
    - `canMonopallet` — boolean. Тип упаковки **Монопаллета**: - `true` — доступен - `false` — недоступен
    - `canSupersafe` — boolean. Тип упаковки **Суперсейф**: - `true` — доступен - `false` — недоступен
    - `isBoxOnPallet` — boolean. Тип поставки **Поштучная палета**: - `true` — доступен - `false` — недоступен
    - `warehouseID` — integer. ID склада. По нему можно получить [информацию о складе](./orders-fbw#tag/informationForFormingSupplies/operation/getV1Warehouses)

**400** — Некорректный запрос

- `detail` — string. Описание ошибки
- `origin` — string. Сервис, вернувший ошибку
- `requestId` — string. ID запроса
- `status` — integer. HTTP статус-код
- `title` — string. ID ошибки

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

**404** — Не найдено

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
