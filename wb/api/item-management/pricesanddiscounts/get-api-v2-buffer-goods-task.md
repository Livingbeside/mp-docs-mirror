---
title: Детализация необработанной загрузки
api: wb-item-management
method: GET
path: /api/v2/buffer/goods/task
operation_id: getV2BufferGoodsTask
tags:
  - pricesAndDiscounts
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 0a4689b0ad0e431c
---

# Детализация необработанной загрузки

`GET /api/v2/buffer/goods/task`

Описание метода

Метод возвращает информацию о товарах и ошибках в товарах из загрузки в обработке.

 Необработанная загрузка — это загрузка скидок в [календаре акций](./promotion#tag/promoCalendar). Такие скидки применятся к товарам только в момент старта акции.

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
  - `bufferGoods` — array[object]. Информация о товарах в загрузке
    - `nmID` — integer. Артикул WB
    - `vendorCode` — string. Артикул продавца
    - `sizeID` — integer. ID размера. В методах Контента это поле `chrtID`
    - `techSizeName` — string. Размер
    - `price` — integer. Цена
    - `currencyIsoCode4217` — string. Валюта, по стандарту ISO 4217
    - `discount` — integer. Скидка, %
    - `clubDiscount` — integer. Скидка WB Клуба, %
    - `status` — integer. Статус товара: `1` — в обработке
    - `errorText` — string. Описание ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**400** — Неправильный запрос

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

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
- `errorText` — string. Описание ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
