---
title: Тарифы — все методы
api: wb-wb-tariffs
spec_version: rates
operations: 5
source: "https://dev.wildberries.ru/docs/openapi/wb-tariffs"
content_sha: 3e5f3fa2b889dbd7
---

# Тарифы

Узнать больше о тарифах можно в справочном центре

В разделе описаны методы получения:
 1. [Комиссий](./wb-tariffs#tag/fees)
 2. [Тарифов на поставку](./wb-tariffs#tag/supplyRates)
 3. [Тарифов на остаток](./wb-tariffs#tag/stockRates)
 4. [Тарифов на возврат товаров продавцу](./wb-tariffs#tag/returnCostToSeller)

Версия спеки: `rates` · методов: **5**

Источник: https://dev.wildberries.ru/docs/openapi/wb-tariffs

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/api/tariffs/v1/acceptance/coefficients` | supplyRates | [Тарифы на поставку](supplyrates/get-api-tariffs-v1-acceptance-coefficients.md) |
| `GET` | `/api/v1/tariffs/box` | stockRates | [Тарифы для коробов](stockrates/get-api-v1-tariffs-box.md) |
| `GET` | `/api/v1/tariffs/commission` | fees | [Комиссия по категориям товаров](fees/get-api-v1-tariffs-commission.md) |
| `GET` | `/api/v1/tariffs/pallet` | stockRates | [Тарифы для монопаллет](stockrates/get-api-v1-tariffs-pallet.md) |
| `GET` | `/api/v1/tariffs/return` | returnCostToSeller | [Тарифы на возврат](returncosttoseller/get-api-v1-tariffs-return.md) |
