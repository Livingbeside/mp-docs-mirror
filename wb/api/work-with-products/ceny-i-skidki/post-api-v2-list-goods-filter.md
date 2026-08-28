---
title: Получить товары с ценами по артикулам
api: wb-work-with-products
method: POST
path: /api/v2/list/goods/filter
operation_id: post-api-v2-list-goods-filter
tags:
  - Цены и скидки
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: f2b8949e95c6185e
---

# Получить товары с ценами по артикулам

`POST /api/v2/list/goods/filter`

Описание метода

Метод возвращает информацию о товарах по их артикулам: цены, валюту, общие скидки, [скидки WB Клуба](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1upload~1task~1club-discount/post) и [оптовые скидки для B2B-продаж](./work-with-products#tag/Ceny-i-skidki/operation/postV1UploadTaskB2bWholesale).

В одном запросе можно указать более одного артикула.

Используйте отдельные методы, чтобы получить информацию:
 - обо [всех товарах продавца, не указывая артикулы](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1list~1goods~1filter/get)
 - о [размерах товара](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1list~1goods~1size~1nm/get)

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

- `nmList` — array[integer] **обязательный**. Артикулы WB для поиска товара

## Ответы

**200** — Успешно

- `data` — object **обязательный**. Данные ответа
  - `listGoods` — array[object] **обязательный**. Информация о товарах
    - `clubDiscount` — integer. Скидка WB Клуба, %
    - `currencyIsoCode4217` — string. Валюта, по стандарту ISO 4217
    - `discount` — integer. Скидка, %
    - `editableSizePrice` — boolean. Можно ли устанавливать цены отдельно для разных размеров (зависит от категории товара): - `true` — можно - `false` — нельзя
    - `isBadTurnover` — boolean. Признак неликвидного товара: - `true` — неликвидный товар с [низким индексом остатка](https://seller.wildberries.ru/instructions/ru/ru/material/stocks-index?categoryId=e324ce0f-9a2a-4b8d-8fd1-72f751b09b3b&goBackOption=prevRoute#%D1%83%D1%80%D0%BE%D0%B2%D0%BD%D0%B8-%D0%B8%D0%BD%D0%B4%D0%B5%D0%BA%D1%81%D0%B0-%D0%BE%D1%81%D1%82%D0%B0%D1%82%D0%BA%D0%B0) - Поле отсутствует — ликвидный товар
    - `nmID` — integer. Артикул WB
    - `sizes` — array[object]. Размер
      - `clubDiscountedPrice` — number **обязательный**. Цена со скидкой, включая скидку WB Клуба
      - `discountedPrice` — number **обязательный**. Цена со скидкой
      - `price` — integer **обязательный**. Цена
      - `sizeID` — integer<int64> **обязательный**. ID размера. В методах Контента это поле `chrtID`
      - `techSizeName` — string **обязательный**. Размер товара
    - `vendorCode` — string. Артикул продавца
    - `wholesaleDiscountThreshold` — array[object]. Оптовые скидки разных уровней для B2B
      - `level` — integer **обязательный**. Уровень скидки
      - `minQuantity` — integer **обязательный**. Минимальное количество единиц товара для скидки
      - `wholesaleDiscount` — integer **обязательный**. Скидка, %
- `error` — boolean **обязательный**. Флаг ошибки
- `errorText` — string **обязательный**. Текст ошибки

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

**402** — Требуется платёж

- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)
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
