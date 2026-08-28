---
title: Тарифы для коробов{{ /api/v1/tariffs/box }}
api: wb-wb-tariffs
method: GET
path: /api/v1/tariffs/box
operation_id: getV1TariffsBox
tags:
  - stockRates
spec_version: rates
source: "https://dev.wildberries.ru/docs/openapi/wb-tariffs"
deprecated: false
content_sha: 9498202178fc1896
---

# Тарифы для коробов{{ /api/v1/tariffs/box }}

`GET /api/v1/tariffs/box`

Описание метода Для остатков товаров, которые поставляются на склад в коробах, метод возвращает [тарифы](https://seller.wildberries.ru/dynamic-product-categories) на: - доставку со склада или пункта приёма до покупателя - доставку от покупателя до пункта приёма - хранение на складе WB Тарифы для коробов совпадают с тарифами для Суперсейфа Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 60 запросов | 1 сек | 5 запросов | | Сервисный | 1 мин | 60 запросов | 1 сек | 5 запросов | | Базовый с секретом | 1 мин | 60 запросов | 1 сек | 5 запросов | | Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `date` | query | string | да | Дата в формате ГГГГ-ММ-ДД |

## Ответы

**200** — Успешно

- `response` — object
  - `data` — object
    - `currency` — string. Валюта тарифов
    - `dtNextBox` — string. Дата начала следующего тарифа
    - `dtTillMax` — string. Дата окончания последнего установленного тарифа
    - `warehouseList` — array[object]. Тарифы для коробов, сгруппированные по складам
      - `boxDeliveryBase` — string. Логистика, первый литр, ₽
      - `boxDeliveryCoefExpr` — string. Коэффициент **Логистика**, %. На него умножается стоимость логистики. Уже учтён в тарифах
      - `boxDeliveryLiter` — string. Логистика, дополнительный литр, ₽
      - `boxDeliveryMarketplaceBase` — string. Логистика FBS, первый литр, ₽
      - `boxDeliveryMarketplaceCoefExpr` — string. Коэффициент **FBS**, %. На него умножается стоимость логистики FBS. Уже учтён в тарифах
      - `boxDeliveryMarketplaceLiter` — string. Логистика FBS, дополнительный литр, ₽
      - `boxStorageBase` — string. Хранение в день, первый литр, ₽
      - `boxStorageCoefExpr` — string. Коэффициент **Хранение**, %. На него умножается стоимость хранения в день. Уже учтён в тарифах
      - `boxStorageLiter` — string. Хранение в день, дополнительный литр, ₽
      - `geoName` — string. Местонахождение склада
      - `warehouseName` — string. Название склада

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
