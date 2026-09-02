---
title: Тарифы для монопаллет
api: wb-rates
method: GET
path: /api/v1/tariffs/pallet
operation_id: getV1TariffsPallet
tags:
  - stockRates
spec_version: rates
source: "https://dev.wildberries.ru/docs/openapi/rates"
deprecated: false
content_sha: 94dc2261333cd056
---

# Тарифы для монопаллет

`GET /api/v1/tariffs/pallet`

Описание метода

Для товаров, которые поставляются на склад WB на монопаллетах, метод возвращает [стоимость](https://seller.wildberries.ru/dynamic-product-categories):
 - доставки со склада до покупателя
 - доставки от покупателя до склада
 - хранения на складе WB

 Тарифы для монопаллет совпадают с тарифами для Поштучных паллет

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 60 запросов | 1 сек | 5 запросов |
| Сервисный | 1 мин | 60 запросов | 1 сек | 5 запросов |
| Базовый с секретом | 1 мин | 60 запросов | 1 сек | 5 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `date` | query | string | да | Дата в формате ГГГГ-ММ-ДД |

## Ответы

**200** — Успешно

- `response` — object
  - `data` — object
    - `currency` — string. Валюта тарифов
    - `dtNextPallet` — string. Дата начала следующего тарифа
    - `dtTillMax` — string. Дата окончания последнего установленного тарифа
    - `warehouseList` — array[object]. Тарифы для монопаллет, сгруппированные по складам
      - `palletDeliveryExpr` — string. Коэффициент доставки, %. На него умножается стоимость доставки. Во всех тарифах этот коэффициент уже учтён
      - `palletDeliveryValueBase` — string. Доставка 1 литра, ₽
      - `palletDeliveryValueLiter` — string. Доставка каждого дополнительного литра, ₽
      - `palletStorageExpr` — string. Коэффициент хранения, %. На него умножается стоимость хранения. Во всех тарифах этот коэффициент уже учтён
      - `palletStorageValueExpr` — string. Хранение 1 монопаллеты, ₽
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
