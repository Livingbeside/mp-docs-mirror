---
title: Тарифы на поставку
api: wb-wb-tariffs
method: GET
path: /api/tariffs/v1/acceptance/coefficients
operation_id: getV1AcceptanceCoefficients
tags:
  - supplyRates
spec_version: rates
source: "https://dev.wildberries.ru/docs/openapi/wb-tariffs"
deprecated: false
content_sha: 6725068779702e99
---

# Тарифы на поставку

`GET /api/tariffs/v1/acceptance/coefficients`

Описание метода

Метод [временно отключён](https://dev.wildberries.ru/release-notes?id=570)

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 6 запросов | 10 сек | 6 запросов |
| Сервисный | 1 мин | 6 запросов | 10 сек | 6 запросов |
| Базовый с секретом | 1 мин | 6 запросов | 10 сек | 6 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `warehouseIDs` | query | string | нет | ID складов. По умолчанию возвращаются данные по всем складам |

## Ответы

**200** — Успешно

- `allowUnload` — boolean. Доступность приёмки для поставок данного типа, смотри значение поля `boxTypeID`: - `true` — приёмка доступна - `false` — приёмка не доступна
- `boxTypeID` — integer. ID типа поставки: - `2` — Короба - `5` — Монопаллеты - `6` — Суперсейф Для типа поставки **QR-поставка с коробами** поле не возвращается
- `coefficient` — number. Коэффициент приёмки: - `-1` — приёмка недоступна, вне зависимости от значения поля `allowUnload` - `0` — бесплатная приёмка - от `1` — множитель стоимости приёмки
- `date` — string. Дата начала действия коэффициента
- `deliveryAdditionalLiter` — string. Стоимость логистики каждого следующего литра
- `deliveryBaseLiter` — string. Стоимость логистики первого литра
- `deliveryCoef` — string. Коэффициент логистики
- `isSortingCenter` — boolean. Тип склада: - `true` — сортировочный центр (СЦ) - `false` — обычный
- `storageAdditionalLiter` — string. Стоимость хранения каждого последующего литра: - для паллет — всегда будет `null`, т.к. стоимость хранения за единицу паллеты определяется в `StorageBaseLiter` - для коробов — стоимость хранения за каждый последующий литр
- `storageBaseLiter` — string. Стоимость хранения: - для паллет — стоимость за одну паллету - для коробов — стоимость хранения за первый литр
- `storageCoef` — string. Коэффициент хранения
- `warehouseID` — integer. ID склада. По нему можно получить [информацию о складе](./orders-fbw#tag/informationForFormingSupplies/operation/getV1Warehouses)
- `warehouseName` — string. Название склада

**400** — Неправильный запрос

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
