---
title: Получить товары в карантине
api: wb-item-management
method: GET
path: /api/v2/quarantine/goods
operation_id: getV2QuarantineGoods
tags:
  - pricesAndDiscounts
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 27a780d4824eeaf0
---

# Получить товары в карантине

`GET /api/v2/quarantine/goods`

Описание метода

Метод возвращает информацию о товарах в карантине.

Если новая цена товара со скидкой будет меньше [порогового значения](https://seller.wildberries.ru/instructions/ru/ru/material/price-quarantine#2ef3641a-5165-41db-9ac7-e4374c9fc3f1), товар попадёт в [карантин](https://seller.wildberries.ru/instructions/ru/ru/material/price-quarantine) и будет продаваться по старой цене. Ошибка об этом будет в [детализации загрузки](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryGoodsTask).

Вы можете изменить цену или скидку с помощью API либо вывести товар из карантина в [личном кабинете](https://seller.wildberries.ru/discount-and-prices/quarantine).

Для товаров с [поразмерной установкой цен](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTaskSize) карантин не применяется.

В [песочнице](/sandbox) товары автоматически удаляются из карантина через 3 дня.

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

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `quarantineGoods` — array[object]. Информация о товарах в карантине
    - `nmID` — integer. Артикул WB
    - `sizeID` — integer. Не используется
    - `techSizeName` — string. Не используется
    - `currencyIsoCode4217` — string. Валюта по стандарту ISO 4217
    - `newPrice` — number<float>. Новая цена продавца до скидки
    - `oldPrice` — number<float>. Текущая цена продавца до скидки
    - `newDiscount` — integer. Новая скидка продавца, %
    - `oldDiscount` — integer. Текущая скидка продавца, %
    - `priceDiff` — number<float>. Разница: `newPrice` * (1 - `newDiscount` / 100) - `oldPrice` * (1 - `oldDiscount` / 100)
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

**402** — Требуется платёж

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)

**403** — Доступ запрещён

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**422** — Неожидаемый результат

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
