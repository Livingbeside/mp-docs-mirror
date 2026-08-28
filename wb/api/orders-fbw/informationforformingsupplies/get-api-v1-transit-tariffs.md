---
title: Транзитные направления{{ /api/v1/transit-tariffs }}
api: wb-orders-fbw
method: GET
path: /api/v1/transit-tariffs
operation_id: getV1TransitTariffs
tags:
  - informationForFormingSupplies
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: c740dc83c6b2151a
---

# Транзитные направления{{ /api/v1/transit-tariffs }}

`GET /api/v1/transit-tariffs`

Описание метода Метод [временно отключён](https://dev.wildberries.ru/release-notes?id=570) Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 6 запросов | 10 сек | 10 запросов | | Сервисный | 1 мин | 6 запросов | 10 сек | 10 запросов | | Базовый с секретом | 1 мин | 6 запросов | 10 сек | 10 запросов | | Базовый | 12 ч | 1 запрос | 12 ч | 1 запрос |

## Ответы

**200** — Успешно

- `transitWarehouseName` — string. Транзитный склад
- `destinationWarehouseName` — string. Склад назначения
- `activeFrom` — string<date-time>. С какого числа доступно транзитное направление
- `boxTariff` — array[object]. Тариф за транзит коробов. Если `null`, транзит для коробов недоступен
  - `from` — integer. Объём поставки от, литры
  - `to` — integer. Объём поставки до, литры
  - `value` — number. Тариф, ₽ за литр
- `palletTariff` — integer. Тариф за паллету, ₽

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
