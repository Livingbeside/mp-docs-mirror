---
title: Получить товары с ценами
api: wb-item-management
method: GET
path: /api/v2/list/goods/filter
operation_id: getV2ListGoodsFilter
tags:
  - pricesAndDiscounts
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 2a8dffc4e59313ce
---

# Получить товары с ценами

`GET /api/v2/list/goods/filter`

Описание метода

Метод возвращает информацию о товарах: цены, валюту, общие скидки, [скидки WB Клуба](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTaskClubDiscount) и [оптовые скидки для B2B-продаж](./item-management#tag/pricesAndDiscounts/operation/postV1UploadTaskB2bWholesale).

В одном запросе можно указать только один артикул.

Чтобы получить информацию обо всех товарах продавца, не указывая артикулы, установите `limit=1000`, в параметре `offset` установите смещение по количеству записей. Количество нужно рассчитать по формуле: `offset` плюс `limit` из предыдущего запроса. Повторяйте запрос, пока вы не получите ответ с пустым массивом.

Используйте отдельные методы, чтобы получить информацию:
 - о [нескольких товарах по артикулам](./item-management#tag/pricesAndDiscounts/operation/postV2ListGoodsFilter)
 - о [размерах товара](./item-management#tag/pricesAndDiscounts/operation/getV2ListGoodsSizeNm)

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
| `filterNmID` | query | integer | нет | Артикул WB для поиска товара |

## Ответы

**200** — Успешно

- `data` — object **обязательный**. Данные ответа
  - `listGoods` — array[object] **обязательный**. Информация о товарах
    - `nmID` — integer. Артикул WB
    - `vendorCode` — string. Артикул продавца
    - `sizes` — array[object]. Размер
      - `sizeID` — integer<int64> **обязательный**. ID размера. В методах Контента это поле `chrtID`
      - `price` — integer **обязательный**. Цена
      - `discountedPrice` — number **обязательный**. Цена со скидкой
      - `clubDiscountedPrice` — number **обязательный**. Цена со скидкой, включая скидку WB Клуба
      - `techSizeName` — string **обязательный**. Размер товара
    - `currencyIsoCode4217` — string. Валюта, по стандарту ISO 4217
    - `discount` — integer. Скидка, %
    - `clubDiscount` — integer. Скидка WB Клуба, %
    - `editableSizePrice` — boolean. Можно ли устанавливать цены отдельно для разных размеров (зависит от категории товара): - `true` — можно - `false` — нельзя
    - `wholesaleDiscountThreshold` — array[object]. Оптовые скидки разных уровней для B2B
      - `minQuantity` — integer **обязательный**. Минимальное количество единиц товара для скидки
      - `wholesaleDiscount` — integer **обязательный**. Скидка, %
      - `level` — integer **обязательный**. Уровень скидки
- `error` — boolean **обязательный**. Флаг ошибки
- `errorText` — string **обязательный**. Текст ошибки

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
