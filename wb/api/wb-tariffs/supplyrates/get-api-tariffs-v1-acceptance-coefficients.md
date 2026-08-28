---
title: Тарифы на поставку{{ /api/tariffs/v1/acceptance/coefficients }}
api: wb-wb-tariffs
method: GET
path: /api/tariffs/v1/acceptance/coefficients
operation_id: getV1AcceptanceCoefficients
tags:
  - supplyRates
spec_version: rates
source: "https://dev.wildberries.ru/docs/openapi/wb-tariffs"
deprecated: false
content_sha: b6a72258578f479a
---

# Тарифы на поставку{{ /api/tariffs/v1/acceptance/coefficients }}

`GET /api/tariffs/v1/acceptance/coefficients`

Описание метода Метод [временно отключён](https://dev.wildberries.ru/release-notes?id=570) Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 6 запросов | 10 сек | 6 запросов | | Сервисный | 1 мин | 6 запросов | 10 сек | 6 запросов | | Базовый с секретом | 1 мин | 6 запросов | 10 сек | 6 запросов | | Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `warehouseIDs` | query | string | нет | ID складов. По умолчанию возвращаются данные по всем складам |

## Ответы

**200** — Успешно

- `date` — string. Дата начала действия коэффициента
- `coefficient` — number. Коэффициент приёмки: - `-1` — приёмка недоступна, вне зависимости от значения поля `allowUnload` - `0` — бесплатная приёмка - от `1` — множитель стоимости приёмки
- `warehouseID` — integer. ID склада. По нему можно получить [информацию о складе](./orders-fbw#tag/informationForFormingSupplies/operation/getV1Warehouses)
- `warehouseName` — string. Название склада
- `allowUnload` — boolean. Доступность приёмки для поставок данного типа, смотри значение поля `boxTypeID`: - `true` — приёмка доступна - `false` — приёмка не доступна
- `boxTypeID` — integer. ID типа поставки: - `2` — Короба - `5` — Монопаллеты - `6` — Суперсейф Для типа поставки **QR-поставка с коробами** поле не возвращается
- `storageCoef` — string. Коэффициент хранения
- `deliveryCoef` — string. Коэффициент логистики
- `deliveryBaseLiter` — string. Стоимость логистики первого литра
- `deliveryAdditionalLiter` — string. Стоимость логистики каждого следующего литра
- `storageBaseLiter` — string. Стоимость хранения: - для паллет — стоимость за одну паллету - для коробов — стоимость хранения за первый литр
- `storageAdditionalLiter` — string. Стоимость хранения каждого последующего литра: - для паллет — всегда будет `null`, т.к. стоимость хранения за единицу паллеты определяется в `StorageBaseLiter` - для коробов — стоимость хранения за каждый последующий литр
- `isSortingCenter` — boolean. Тип склада: - `true` — сортировочный центр (СЦ) - `false` — обычный

**400** — Неправильный запрос

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
