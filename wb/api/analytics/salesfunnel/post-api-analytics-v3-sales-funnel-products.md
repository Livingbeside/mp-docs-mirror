---
title: Статистика карточек товаров за период
api: wb-analytics
method: POST
path: /api/analytics/v3/sales-funnel/products
operation_id: postV3SalesFunnelProducts
tags:
  - salesFunnel
spec_version: analytics
source: "https://dev.wildberries.ru/docs/openapi/analytics"
deprecated: false
content_sha: d3452c6dac171b79
---

# Статистика карточек товаров за период

`POST /api/analytics/v3/sales-funnel/products`

Описание метода

Метод формирует отчёт о товарах, сравнивая ключевые показатели за текущий период с аналогичным прошлым.

Данные отчёта обновляются 1 раз в час.

В течение часа после события появляется большая часть данных:
 - о заказах
 - о переходах в карточку товара
 - о добавлениях товаров в корзину

Малая часть этих данных может появляться в течение нескольких дней.

Выкупы, отмены и возвраты отображаются в отчёте за тот день, когда товар был заказан. Например, если заказ был сделан 1 января, а покупатель вернул товар 10 января, данные об этом возврате появятся в отчёте за 1 января.

Окончательные итоги продаж вы можете отслеживать с помощью [детализаций к отчётам реализации](./financial-reports-and-accounting#tag/financialReports).

Параметры `brandNames`,`subjectIds`, `tagIds`, `nmIds` могут быть пустыми `[]`, тогда в ответе возвращаются все карточки продавца.

Если вы указали несколько параметров, в ответе будут карточки, в которых есть одновременно все эти параметры. Если карточки не подходят по параметрам запроса, вернётся пустой ответ `[]`.

Можно получить отчёт максимум за последние 365 дней.

В данных предыдущего периода:
 * Данные в `pastPeriod` указаны за такой же период, что и в `selectedPeriod`
 * Если дата начала `pastPeriod` раньше, чем год назад от текущей даты, она будет приведена к виду: `pastPeriod.start = текущая дата — 365 дней`

Можно использовать пагинацию.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 3 запроса | 20 сек | 3 запроса |
| Сервисный | 1 мин | 3 запроса | 20 сек | 3 запроса |
| Базовый с секретом | 1 мин | 3 запроса | 20 сек | 3 запроса |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `brandNames` — array[string]. Список брендов для фильтрации
- `limit` — integer<uint32>. Количество карточек товара в ответе По умолчанию: `50`.
- `nmIds` — array[integer<uint64>]. Артикулы WB, по которым нужно составить отчёт. Оставьте пустым, чтобы получить отчёт обо всех товарах
- `offset` — integer<uint32>. Сколько элементов пропустить. Например, для значения `10` ответ начнётся с 11 элемента По умолчанию: `0`.
- `orderBy` — object. Параметры сортировки
  - `field` — string (openCard, addToCart, orderCount, orderSum, buyoutCount, buyoutSum, cancelCount, cancelSum, avgPrice, stockMpQty, stockWbQty, shareOrderPercent…) **обязательный**. Поле для сортировки: - `openCard` — Перешли в карточку - `addToCart` — Положили в корзину - `orderCount` — Заказали товаров, шт - `orderSum` — Заказали на сумму - `buyoutCount` — Выкупили товаров, шт - `buyoutSum` — Выкупили на сумму - `cancelCount` — Отменили и вернули товаров, шт - `cancelSum` — Отменили и вернули на сумму - `avgPrice` — Средняя цена - `stockMpQty` — Остатки на складах продавца, шт - `stockWbQty` — Остатки на складах WB, шт - `shareOrderPercent` — Доля в выручке - `addToWishlist` — Добавили в **Отложенные** - `timeToReady` — Среднее время доставки - `localizationPercent` — Локальные заказы в рамках одного региона - `wbClub.orderCount` — Заказали товаров с WB Клубом, шт - `wbClub.orderSum` — Заказали с WB Клубом на сумму - `wbClub.buyoutSum` — Выкупили товаров с WB Клубом, шт - `wbClub.buyoutCount` — Процент выкупа с WB Клубом - `wbClub.cancelSum` — Отменили и вернули товаров с WB Клубом на сумму - `wbClub.avgPrice` — Средняя цена с WB Клубом - `wbClub.buyoutPercent` — Процент выкупа с WB Клубом - `wbClub.avgOrderCountPerDay` — Среднее количество заказов в день с WB Клубом, шт - `wbClub.cancelCount` — Отменили и вернули товаров с WB Клубом, шт По умолчанию: `openCard`.
  - `mode` — string (asc, desc) **обязательный**. Порядок сортировки: - `asc` — по возрастанию - `desc` — по убыванию По умолчанию: `desc`.
- `pastPeriod` — object
  - `end` — string<date> **обязательный**. Конец периода
  - `start` — string<date> **обязательный**. Начало периода
- `selectedPeriod` — object **обязательный**
  - `end` — string<date> **обязательный**. Конец периода
  - `start` — string<date> **обязательный**. Начало периода
- `skipDeletedNm` — boolean. Скрыть удалённые товары
- `subjectIds` — array[integer<uint64>]. Список ID предметов для фильтрации
- `tagIds` — array[integer<uint64>]. Список ID ярлыков для фильтрации

## Ответы

**200** — Успешно

- `data` — object **обязательный**
  - `currency` — string **обязательный**. Валюта отчёта
  - `products` — array[object] **обязательный**. Список карточек товаров
    - `product` — object **обязательный**
      - `brandName` — string **обязательный**. Бренд
      - `feedbackRating` — number<float32> **обязательный**. Оценка пользователей
      - `nmId` — integer<int64> **обязательный**. Артикул WB
      - `productRating` — number<float32> **обязательный**. Оценка карточки
      - `stocks` — object **обязательный**. Остатки
        - `balanceSum` — integer<uint32> **обязательный**. Сумма остатков на складах на текущий день, шт.
        - `mp` — integer<uint32> **обязательный**. Общее количество остатков на складах продавца на текущий день, шт.
        - `wb` — integer<uint32> **обязательный**. Общее количество остатков на складах WB на текущий день, шт.
      - `subjectId` — integer<uint64> **обязательный**. ID предмета
      - `subjectName` — string **обязательный**. Название предмета
      - `tags` — array[object] **обязательный**. Ярлыки
        - `id` — integer<uint64> **обязательный**. ID ярлыка
        - `name` — string **обязательный**. Название ярлыка
      - `title` — string<int64> **обязательный**. Название карточки товара
      - `vendorCode` — string **обязательный**. Артикул продавца
    - `statistic` — object **обязательный**
      - `comparison` — object
        - `addToWishlistDynamic` — integer<int> **обязательный**. Динамика добавлений товара в избранное
        - `avgOrdersCountPerDayDynamic` — integer<int> **обязательный**. Динамика среднего количества заказов в день
        - `avgPriceDynamic` — integer<int> **обязательный**. Динамика средней цены на товары. Учитываются скидки для акций
        - `buyoutCountDynamic` — integer<int> **обязательный**. Динамика выкупов
        - `buyoutSumDynamic` — integer<int> **обязательный**. Динамика суммы выкупов
        - `cancelCountDynamic` — integer<int> **обязательный**. Динамика отмен и возвратов товаров
        - `cancelSumDynamic` — integer<int> **обязательный**. Динамика сумм отмен и возвратов товаров
        - `cartCountDynamic` — integer<int> **обязательный**. Динамика добавлений в корзину
        - `conversions` — object **обязательный**
          - `addToCartPercent` — integer<int> **обязательный**. Конверсия в корзину. Какой процент посетителей, открывших карточку товара, добавили товар в корзину, %
          - `buyoutPercent` — integer<int> **обязательный**. Процент выкупа. Какой процент посетителей, заказавших товар, его выкупили. Без учёта товаров, которые еще доставляются покупателю, %
          - `cartToOrderPercent` — integer<int> **обязательный**. Конверсия в заказ. Какой процент посетителей, добавивших товар в корзину, сделали заказ, %
        - `localizationPercentDynamic` — integer<int> **обязательный**. Динамика локальных заказов в рамках одного региона. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `0`
        - `openCountDynamic` — integer<int> **обязательный**. Динамика переходов в карточку товара
        - `orderCountDynamic` — integer<int> **обязательный**. Динамика количества заказов
        - `orderSumDynamic` — integer<int> **обязательный**. Динамика суммы заказов
        - `shareOrderPercentDynamic` — integer<int> **обязательный**. Динамика доли в выручке
        - `timeToReadyDynamic` — object **обязательный**
          - `days` — integer **обязательный**. Дни
          - `hours` — integer **обязательный**. Часы
          - `mins` — integer **обязательный**. Минуты
        - `wbClubDynamic` — object **обязательный**
          - `avgOrderCountPerDay` — number<int> **обязательный**. Динамика среднего количества заказов с WB Клубом в день
          - `avgPrice` — integer<int> **обязательный**. Динамика средней цены на товары с WB Клубом
          - `buyoutCount` — integer<int> **обязательный**. Динамика выкупов с WB Клубом
          - `buyoutPercent` — integer<int> **обязательный**. Динамика процента выкупа с WB Клубом
          - `buyoutSum` — integer<int> **обязательный**. Динамика суммы выкупов с WB Клубом
          - `cancelCount` — integer<int> **обязательный**. Динамика отмен и возвратов товаров с WB Клубом
          - `cancelSum` — integer<int> **обязательный**. Динамика сумм отмен и возвратов товаров с WB Клубом
          - `orderCount` — integer<int> **обязательный**. Динамика количества заказов с WB Клубом
          - `orderSum` — integer<int> **обязательный**. Динамика суммы заказов с WB Клубом
      - `past` — object
        - `addToWishlist` — integer **обязательный**. Добавили в **Отложенные**
        - `avgOrdersCountPerDay` — number<float64> **обязательный**. Среднее количество заказов в день, шт.
        - `avgPrice` — integer<uint32> **обязательный**. Средняя цена
        - `buyoutCount` — integer<uint32> **обязательный**. Выкупили товаров, шт.
        - `buyoutSum` — integer<uint32> **обязательный**. Выкупили на сумму
        - `cancelCount` — integer<uint32> **обязательный**. Отменили и вернули товаров, шт.
        - `cancelSum` — integer<uint32> **обязательный**. Отменили и вернули на сумму
        - `cartCount` — integer<int32> **обязательный**. Положили в корзину, шт.
        - `conversions` — object **обязательный**
          - `addToCartPercent` — integer<int> **обязательный**. Конверсия в корзину. Какой процент посетителей, открывших карточку товара, добавили товар в корзину, %
          - `buyoutPercent` — integer<int> **обязательный**. Процент выкупа. Какой процент посетителей, заказавших товар, его выкупили. Без учёта товаров, которые еще доставляются покупателю, %
          - `cartToOrderPercent` — integer<int> **обязательный**. Конверсия в заказ. Какой процент посетителей, добавивших товар в корзину, сделали заказ, %
        - `localizationPercent` — integer **обязательный**. Локальные заказы в рамках одного региона. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `100`
        - `openCount` — integer<uint32> **обязательный**. Количество переходов в карточку товара
        - `orderCount` — integer<uint32> **обязательный**. Заказали товаров, шт.
        - `orderSum` — integer<uint32> **обязательный**. Заказали на сумму
        - `period` — object **обязательный**
          - `end` — string<date> **обязательный**. Конец периода
          - `start` — string<date> **обязательный**. Начало периода
        - `shareOrderPercent` — number<float64> **обязательный**. Доля в выручке
        - `timeToReady` — object **обязательный**
          - `days` — integer **обязательный**. Дни
          - `hours` — integer **обязательный**. Часы
          - `mins` — integer **обязательный**. Минуты
        - `wbClub` — object **обязательный**
          - `avgOrderCountPerDay` — number<float64> **обязательный**. Среднее количество заказов с WB Клубом в день, шт.
          - `avgPrice` — integer<uint32> **обязательный**. Средняя цена с WB Клубом
          - `buyoutCount` — integer<uint32> **обязательный**. Выкупили товаров с WB Клубом, шт.
          - `buyoutPercent` — integer<uint32> **обязательный**. Процент выкупа с WB Клубом
          - `buyoutSum` — integer<uint32> **обязательный**. Выкупили с WB Клубом на сумму
          - `cancelCount` — integer<uint32> **обязательный**. Отменили и вернули товаров с WB Клубом, шт.
          - `cancelSum` — integer<uint32> **обязательный**. Отменили и вернули с WB Клубом на сумму
          - `orderCount` — integer<uint32> **обязательный**. Заказали товаров с WB Клубом, шт.
          - `orderSum` — integer<uint32> **обязательный**. Заказали с WB Клубом на сумму
      - `selected` — object **обязательный**
        - `addToWishlist` — integer **обязательный**. Добавили в **Отложенные**
        - `avgOrdersCountPerDay` — number<float64> **обязательный**. Среднее количество заказов в день, шт.
        - `avgPrice` — integer<uint32> **обязательный**. Средняя цена
        - `buyoutCount` — integer<uint32> **обязательный**. Выкупили товаров, шт.
        - `buyoutSum` — integer<uint32> **обязательный**. Выкупили на сумму
        - `cancelCount` — integer<uint32> **обязательный**. Отменили и вернули товаров, шт.
        - `cancelSum` — integer<uint32> **обязательный**. Отменили и вернули на сумму
        - `cartCount` — integer<int32> **обязательный**. Положили в корзину, шт.
        - `conversions` — object **обязательный**
          - `addToCartPercent` — integer<int> **обязательный**. Конверсия в корзину. Какой процент посетителей, открывших карточку товара, добавили товар в корзину, %
          - `buyoutPercent` — integer<int> **обязательный**. Процент выкупа. Какой процент посетителей, заказавших товар, его выкупили. Без учёта товаров, которые еще доставляются покупателю, %
          - `cartToOrderPercent` — integer<int> **обязательный**. Конверсия в заказ. Какой процент посетителей, добавивших товар в корзину, сделали заказ, %
        - `localizationPercent` — integer **обязательный**. Локальные заказы в рамках одного региона. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `100`
        - `openCount` — integer<uint32> **обязательный**. Количество переходов в карточку товара
        - `orderCount` — integer<uint32> **обязательный**. Заказали товаров, шт.
        - `orderSum` — integer<uint32> **обязательный**. Заказали на сумму
        - `period` — object **обязательный**
          - `end` — string<date> **обязательный**. Конец периода
          - `start` — string<date> **обязательный**. Начало периода
        - `shareOrderPercent` — number<float64> **обязательный**. Доля в выручке
        - `timeToReady` — object **обязательный**
          - `days` — integer **обязательный**. Дни
          - `hours` — integer **обязательный**. Часы
          - `mins` — integer **обязательный**. Минуты
        - `wbClub` — object **обязательный**
          - `avgOrderCountPerDay` — number<float64> **обязательный**. Среднее количество заказов с WB Клубом в день, шт.
          - `avgPrice` — integer<uint32> **обязательный**. Средняя цена с WB Клубом
          - `buyoutCount` — integer<uint32> **обязательный**. Выкупили товаров с WB Клубом, шт.
          - `buyoutPercent` — integer<uint32> **обязательный**. Процент выкупа с WB Клубом
          - `buyoutSum` — integer<uint32> **обязательный**. Выкупили с WB Клубом на сумму
          - `cancelCount` — integer<uint32> **обязательный**. Отменили и вернули товаров с WB Клубом, шт.
          - `cancelSum` — integer<uint32> **обязательный**. Отменили и вернули с WB Клубом на сумму
          - `orderCount` — integer<uint32> **обязательный**. Заказали товаров с WB Клубом, шт.
          - `orderSum` — integer<uint32> **обязательный**. Заказали с WB Клубом на сумму

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

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

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
