---
title: Транзитные направления
api: wb-orders-fbw
method: GET
path: /api/v1/transit-tariffs
operation_id: getV1TransitTariffs
tags:
  - informationForFormingSupplies
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: 41fcd408a8a67f78
---

# Транзитные направления

`GET /api/v1/transit-tariffs`

Описание метода

Метод [временно отключён](https://dev.wildberries.ru/release-notes?id=570)

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 6 запросов | 10 сек | 10 запросов |
| Сервисный | 1 мин | 6 запросов | 10 сек | 10 запросов |
| Базовый с секретом | 1 мин | 6 запросов | 10 сек | 10 запросов |
| Базовый | 12 ч | 1 запрос | 12 ч | 1 запрос |

## Ответы

**200** — Успешно

- `activeFrom` — string<date-time>. С какого числа доступно транзитное направление
- `boxTariff` — array[object]. Тариф за транзит коробов. Если `null`, транзит для коробов недоступен
  - `from` — integer. Объём поставки от, литры
  - `to` — integer. Объём поставки до, литры
  - `value` — number. Тариф, ₽ за литр
- `destinationWarehouseName` — string. Склад назначения
- `palletTariff` — integer. Тариф за паллету, ₽
- `transitWarehouseName` — string. Транзитный склад

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
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
