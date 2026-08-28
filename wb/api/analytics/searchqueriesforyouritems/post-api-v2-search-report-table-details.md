---
title: Пагинация по товарам в группе
api: wb-analytics
method: POST
path: /api/v2/search-report/table/details
operation_id: postV2SearchReportTableDetails
tags:
  - searchQueriesForYourItems
spec_version: analytics
source: "https://dev.wildberries.ru/docs/openapi/analytics"
deprecated: false
content_sha: cf367e175270ebc0
---

# Пагинация по товарам в группе

`POST /api/v2/search-report/table/details`

Описание метода

Метод формирует дополнительные данные к [основному отчёту](./analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportReport) с пагинацией по товарам в группе. Пагинация возможна вне зависимости от наличия фильтров.

Фильтры для пагинации по товарам в группе или без фильтров:
 - кортеж `subjectId`,`brandName`,`tagId` — фильтр для группы
 - `nmIds` — фильтр по карточке товара

Дополнительный параметр выбора списка товаров:
 - `positionCluster` — средняя позиция в поиске

Параметры `includeSubstitutedSKUs` и `includeSearchTexts` не могут одновременно иметь значение `false`.

Данные отчёта обновляются 1 раз в час.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 3 запроса | 20 сек | 3 запроса |
| Сервисный | 1 мин | 3 запроса | 20 сек | 3 запроса |
| Базовый с секретом | 1 мин | 3 запроса | 20 сек | 3 запроса |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `currentPeriod` — object **обязательный**. Текущий период
  - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 365 суток от сегодня
  - `end` — string<date> **обязательный**. Дата окончания периода. Не ранее 365 суток от сегодня
- `pastPeriod` — object. Прошлый период для сравнения. Количество дней — меньше или равно `currentPeriod`
  - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 365 суток от сегодня
  - `end` — string<date> **обязательный**. Дата окончания периода. Не позднее даты перед датой начала `currentPeriod`. Не ранее 365 суток от сегодня
- `subjectId` — integer<int32>. ID предмета
- `brandName` — string. Название товара
- `tagId` — integer<int64>. ID ярлыка
- `nmIds` — array[integer<uint64>]. Список артикулов WB
- `orderBy` — object **обязательный**. Параметры сортировки
  - `field` — string (avgPosition, openCard, addToCart, openToCart, orders, cartToOrder, visibility, minPrice, maxPrice) **обязательный**. Поле для сортировки: - `avgPosition` — по средней позиции - `addToCart` — по добавлениям в корзину - `openCard` — по открытию карточки (переход на страницу товара) - `orders` — по количеству заказов - `cartToOrder` — по конверсии в заказ из поиска - `openToCart` — по конверсии в корзину из поиска - `visibility` — по видимости товара - `minPrice` — по минимальной цене - `maxPrice` — по максимальной цене
  - `mode` — string (asc, desc) **обязательный**. Порядок сортировки: - `asc` — по возрастанию - `desc` — по убыванию
- `positionCluster` — string (all, firstHundred, secondHundred, below) **обязательный**. Товары с какой средней позицией в поиске показывать в отчёте: - `all` — все - `firstHundred` — от 1 до 100 - `secondHundred` — от 101 до 200 - `below` — от 201 и ниже
- `includeSubstitutedSKUs` — boolean. Показать данные по прямым запросам с [подменным артикулом](https://seller.wildberries.ru/help-center/article/A-524) По умолчанию: `True`.
- `includeSearchTexts` — boolean. Показать данные по поисковым запросам без учёта подменного артикула По умолчанию: `True`.
- `limit` — integer<uint32> **обязательный**. Количество товаров в ответе
- `offset` — integer<uint32> **обязательный**. После какого элемента выдавать данные

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
- `data` — object **обязательный**
  - `products` — array[object] **обязательный**. Список товаров в группе по фильтру
    - `nmId` — integer<int64>. Артикул WB
    - `name` — string. Название товара
    - `vendorCode` — string. Артикул продавца
    - `subjectName` — string. Название предмета
    - `brandName` — string. Бренд
    - `mainPhoto` — string. URL главного фото карточки товара
    - `isAdvertised` — boolean. Находится ли товар в продвижении в Поисковой выдаче
    - `isSubstitutedSKU` — boolean. Искали ли товар по подменному артикулу. Поле будет в ответе при наличии в запросе `includeSubstitutedSKUs` и/или `includeSearchTexts`
    - `isCardRated` — boolean. Есть ли рейтинг у карточки товара
    - `rating` — number<float64>. Рейтинг карточки товара
    - `feedbackRating` — number<float64>. Рейтинг по отзывам
    - `price` — object. Цена
      - `minPrice` — integer<uint64> **обязательный**. Минимальная цена продавца со скидкой продавца (без учёта скидки WB Клуба)
      - `maxPrice` — integer<uint64> **обязательный**. Максимальная цена продавца со скидкой продавца (без учёта скидки WB Клуба)
    - `avgPosition` — object. Средняя позиция товара в результатах поиска
      - `current` — integer **обязательный**. Текущая средняя позиция
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `openCard` — object. Количество переходов в карточку товара из поиска
      - `current` — integer **обязательный**. Текущее количество переходов
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `addToCart` — object. Сколько раз товар из поиска добавили в корзину
      - `current` — integer **обязательный**. Текущее количество
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `openToCart` — object. Конверсия в корзину из поиска — доля добавлений товара в корзину по отношению ко всем переходам в карточку товара из поиска
      - `current` — integer **обязательный**. Текущая конверсия
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `orders` — object. Сколько раз товары из поиска заказали
      - `current` — integer **обязательный**. Текущее количество
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `cartToOrder` — object. Конверсия в заказ из поиска — доля заказов товара по отношению ко всем добавлениям товара из поиска в корзину
      - `current` — integer **обязательный**. Текущая конверсия
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `visibility` — object. Процент видимости товара в результатах поиска
      - `current` — integer **обязательный**. Текущий процент видимости
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
  - `currency` — string **обязательный**. Валюта отчёта

**400** — Неправильный запрос

- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string **обязательный**. Детали ошибки
- `requestId` — string **обязательный**. Уникальный ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB

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

- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string **обязательный**. Детали ошибки
- `requestId` — string **обязательный**. Уникальный ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
