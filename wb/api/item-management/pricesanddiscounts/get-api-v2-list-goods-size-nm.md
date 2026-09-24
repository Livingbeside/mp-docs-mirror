---
title: Получить размеры товара с ценами
api: wb-item-management
method: GET
path: /api/v2/list/goods/size/nm
operation_id: getV2ListGoodsSizeNm
tags:
  - pricesAndDiscounts
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 54b77a8b9b4a5224
---

# Получить размеры товара с ценами

`GET /api/v2/list/goods/size/nm`

Описание метода

Метод возвращает информацию обо всех размерах одного товара: цены, валюту, общие скидки и скидки для [WB Клуба](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTaskClubDiscount).

Работает только для товаров из категорий, где можно устанавливать цены отдельно для разных размеров. Для таких товаров `"editableSizePrice":true`.

Чтобы получить информацию о самом товаре, используйте [отдельный метод](./item-management#tag/pricesAndDiscounts/operation/getV2ListGoodsFilter).

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
| `nmID` | query | integer | да | Артикул WB |

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `listGoods` — array[object]. Размеры товара
    - `nmID` — integer. Артикул WB
    - `sizeID` — integer. ID размера. Можно получить с помощью метода [Получение списка товаров по артикулам](./item-management#tag/pricesAndDiscounts/operation/getV2ListGoodsFilter), поле `sizeID`. В методах Контента это поле `chrtID`
    - `vendorCode` — string. Артикул продавца
    - `price` — integer. Цена
    - `currencyIsoCode4217` — string. Валюта, по стандарту ISO 4217
    - `discountedPrice` — number. Цена со скидкой
    - `clubDiscountedPrice` — number. Цена со скидкой, включая скидку WB Клуба
    - `discount` — integer. Скидка, %
    - `clubDiscount` — integer. Скидка WB Клуба, %
    - `techSizeName` — string. Размер товара
    - `editableSizePrice` — boolean. Можно ли устанавливать цены отдельно для разных размеров (зависит от категории товара): - `true` — можно - `false` — нельзя
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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
