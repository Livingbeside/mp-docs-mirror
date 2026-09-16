---
title: Комиссия по категориям товаров
api: wb-rates
method: GET
path: /api/v1/tariffs/commission
operation_id: getV1TariffsCommission
tags:
  - fees
spec_version: rates
source: "https://dev.wildberries.ru/docs/openapi/rates"
deprecated: false
content_sha: cd081d1426e23b52
---

# Комиссия по категориям товаров

`GET /api/v1/tariffs/commission`

Описание метода

Метод возвращает данные о [комиссии](https://seller.wildberries.ru/dynamic-product-categories/commission) WB по [родительским категориям товаров](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2ObjectParentAll) согласно модели продаж.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 1 запрос | 1 мин | 2 запроса |
| Сервисный | 1 мин | 1 запрос | 1 мин | 2 запроса |
| Базовый с секретом | 1 мин | 1 запрос | 1 мин | 2 запроса |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `locale` | query | string | нет | Язык полей ответа `parentName` и `subjectName`: - `ru` — русский - `en` — английский - `zh` — китайский |

## Ответы

**200** — Успешно

- `report` — array[object]. Список комиссий
  - `kgvpBooking` — number. Комиссия по модели **Бронирование**, %
  - `kgvpMarketplace` — number. Комиссия по модели **Маркетплейс** (`FBS`), %
  - `kgvpPickup` — number. Комиссия по модели **Самовывоз из магазина продавца** (`C&C`), %
  - `kgvpSupplier` — number. Комиссия по моделям **Витрина** (`DBS`) и **Деливери WB** (`DBW`), %
  - `kgvpSupplierExpress` — number. Комиссия по модели **Витрина экспресс** (`EDBS`), %
  - `paidStorageKgvp` — number. Комиссия по модели **Склад WB** (`FBW`), %
  - `parentID` — integer. ID родительской категории
  - `parentName` — string. Название родительской категории
  - `subjectID` — integer. ID предмета
  - `subjectName` — string. Название предмета
- `report` — array[object]. Список комиссий
  - `kgvpChina` — number. Комиссия для продавцов из Китая, %
  - `parentID` — integer. ID родительской категории
  - `parentName` — string. Название родительской категории
  - `subjectID` — integer. ID предмета
  - `subjectName` — string. Название предмета
- `report` — array[object]. Список комиссий
  - `kgvpTurkey` — number. Комиссия для продавцов из Турции, %
  - `parentID` — integer. ID родительской категории
  - `parentName` — string. Название родительской категории
  - `subjectID` — integer. ID предмета
  - `subjectName` — string. Название предмета
- `report` — array[object]. Список комиссий
  - `kgvpMarketplaceUz` — number. Комиссия по модели **Маркетплейс** (`FBS`), %
  - `kgvpPaidStorageUz` — number. Комиссия по модели **Склад WB** (`FBW`), %
  - `kgvpSupplierUz` — number. Комиссия по модели **Витрина** (`DBS`), %
  - `parentID` — integer. ID родительской категории
  - `parentName` — string. Название родительской категории
  - `subjectID` — integer. ID предмета
  - `subjectName` — string. Название предмета
- `report` — array[object]. Список комиссий
  - `kgvpUAE` — number. Комиссия для продавцов из ОАЭ, %
  - `parentID` — integer. ID родительской категории
  - `parentName` — string. Название родительской категории
  - `subjectID` — integer. ID предмета
  - `subjectName` — string. Название предмета

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
