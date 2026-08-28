---
title: Детализация обработанной загрузки
api: wb-work-with-products
method: GET
path: /api/v2/history/goods/task
operation_id: get-api-v2-history-goods-task
tags:
  - Цены и скидки
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: a81828a395eba9b3
---

# Детализация обработанной загрузки

`GET /api/v2/history/goods/task`

Описание метода

Метод возвращает информацию о товарах и об ошибках в товарах в обработанной загрузке.

 Обработанная загрузка — это загрузка цен и скидок для товаров, цен для размеров товаров скидок WB Клуба и оптовых скидок для B2B-продаж.

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
  - `historyGoods` — array[object]. Информация о товарах в загрузке
    - `clubDiscount` — integer. Скидка WB Клуба, %
    - `currencyIsoCode4217` — string. Валюта, по стандарту ISO 4217
    - `discount` — integer. Скидка, %
    - `errorText` — string. Текст ошибки. Например: - `You can't change the item price. Item was added to the Sale due to high inventory` — ошибка возникает, если товар попал под распродажу по [индексу остатка](https://seller.wildberries.ru/instructions/ru/ru/material/A-1159). - `The new price is several times lower than the current price. Item has been moved to Price Quarantine` — ошибка возникает, если новая цена со скидкой хотя бы в 3 раза меньше старой. Вы можете изменить цену или скидку с помощью API либо вывести товар из карантина в [личном кабинете](https://seller.wildberries.ru/discount-and-prices/quarantine).
    - `nmID` — integer. Артикул WB
    - `price` — integer. Цена
    - `sizeID` — integer. ID размера. В методах Контента это поле `chrtID`
    - `status` — integer. Статус товара: * `2` — товар без ошибок, цена и/или скидка обновилась * `3` — есть ошибки, данные не обновились
    - `techSizeName` — string. Размер
    - `vendorCode` — string. Артикул продавца
  - `uploadID` — integer. ID загрузки

**400** — Неправильный запрос

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**403** — Доступ запрещён

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
