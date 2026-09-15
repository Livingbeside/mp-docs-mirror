---
title: Установить цены для размеров
api: wb-item-management
method: POST
path: /api/v2/upload/task/size
operation_id: postV2UploadTaskSize
tags:
  - pricesAndDiscounts
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: a7136b0ff5bbdcab
---

# Установить цены для размеров

`POST /api/v2/upload/task/size`

Описание метода

Метод устанавливает цены отдельно для размеров товаров.

Работает только для товаров из категорий, где можно устанавливать цены отдельно для разных размеров. Для [таких товаров](./item-management#tag/pricesAndDiscounts/operation/getV2ListGoodsSizeNm) `"editableSizePrice":true`.

Чтобы установить цены и скидки для самих товаров, используйте [отдельный метод](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTask).

 Получить информацию о процессе установки цен и скидок можно с помощью методов [состояния](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryTasks) и [детализации](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryGoodsTask) обработанной загрузки.

Лимит запросов на один аккаунт продавца для всех методов категории Цены и скидки:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Запрос

**Тело запроса** (`application/json`):

- `data` — array[object] **обязательный**. Размеры и цены для них. Максимум 1 000 размеров. Для товаров с поразмерной установкой цен [карантин](https://seller.wildberries.ru/instructions/ru/ru/material/price-quarantine) не применяется
  - `nmID` — integer **обязательный**. Артикул WB
  - `sizeID` — integer **обязательный**. ID размера. Можно получить с помощью методов [Получить товары с ценами](./item-management#tag/pricesAndDiscounts/operation/getV2ListGoodsFilter) и [Получить товары с ценами по артикулам](./item-management#tag/pricesAndDiscounts/operation/postV2ListGoodsFilter), поле `sizeID`. В методах Контента это поле `chrtID`
  - `price` — integer **обязательный**. Цена. Валюту можно получить с помощью методов [Получить товары с ценами](./item-management#tag/pricesAndDiscounts/operation/getV2ListGoodsFilter) и [Получить товары с ценами по артикулам](./item-management#tag/pricesAndDiscounts/operation/postV2ListGoodsFilter), поле `currencyIsoCode4217`

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `id` — integer. ID загрузки
  - `alreadyExists` — boolean. Флаг дублирования загрузки: `true` — такая загрузка уже есть
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**208** — Такая загрузка уже есть

- `data` — object. Данные ответа
  - `id` — integer. ID загрузки
  - `alreadyExists` — boolean. Флаг дублирования загрузки: `true` — такая загрузка уже есть
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**400** — Неправильный запрос

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

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

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**409** — Ошибка при конвертации валюты

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**422** — Неожидаемый результат

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
