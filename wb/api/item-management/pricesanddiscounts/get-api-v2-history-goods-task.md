---
title: Детализация обработанной загрузки
api: wb-item-management
method: GET
path: /api/v2/history/goods/task
operation_id: getV2HistoryGoodsTask
tags:
  - pricesAndDiscounts
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 0b6ebc32fb64a9ff
---

# Детализация обработанной загрузки

`GET /api/v2/history/goods/task`

Описание метода

Метод возвращает информацию о товарах и об ошибках в товарах в обработанной загрузке.

 Обработанная загрузка — это загрузка цен и скидок для [товаров](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTask), цен для [размеров товаров](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTaskSize) [скидок WB Клуба](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTaskClubDiscount) и [оптовых скидок для B2B-продаж](./item-management#tag/pricesAndDiscounts/operation/postV1UploadTaskB2bWholesale).

Лимит запросов на один аккаунт продавца для всех методов категории Цены и скидки:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `limit` | query | integer<uint> | да | Сколько элементов вывести на одной странице (пагинация) |
| `offset` | query | integer<uint> | нет | Сколько элементов пропустить. Например, для значения `10` ответ начнется с 11 элемента |
| `uploadID` | query | integer | да | ID загрузки |

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `uploadID` — integer. ID загрузки
  - `historyGoods` — array[object]. Информация о товарах в загрузке
    - `nmID` — integer. Артикул WB
    - `vendorCode` — string. Артикул продавца
    - `sizeID` — integer. ID размера. В методах Контента это поле `chrtID`
    - `techSizeName` — string. Размер
    - `price` — integer. Цена
    - `currencyIsoCode4217` — string. Валюта, по стандарту ISO 4217
    - `discount` — integer. Скидка, %
    - `clubDiscount` — integer. Скидка WB Клуба, %
    - `status` — integer. Статус товара: * `2` — товар без ошибок, цена и/или скидка обновилась * `3` — есть ошибки, данные не обновились
    - `errorText` — string. Текст ошибки. Например: - `New price is several times lower than the current price. Item has been moved to Price Quarantine` — ошибка возникает, если новая цена со скидкой меньше [порогового значения](https://seller.wildberries.ru/instructions/ru/ru/material/price-quarantine#2ef3641a-5165-41db-9ac7-e4374c9fc3f1). Вы можете изменить цену или скидку с помощью API либо вывести товар из карантина в [личном кабинете](https://seller.wildberries.ru/discount-and-prices/quarantine).

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

**403** — Доступ запрещён

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
