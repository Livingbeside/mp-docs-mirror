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
content_sha: e0e904249e2a8465
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

- `brandName` — string. Название товара
- `currentPeriod` — object **обязательный**. Текущий период
  - `end` — string<date> **обязательный**. Дата окончания периода. Не ранее 365 суток от сегодня
  - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 365 суток от сегодня
- `includeSearchTexts` — boolean. Показать данные по поисковым запросам без учёта подменного артикула По умолчанию: `True`.
- `includeSubstitutedSKUs` — boolean. Показать данные по прямым запросам с [подменным артикулом](https://seller.wildberries.ru/help-center/article/A-524) По умолчанию: `True`.
- `limit` — integer<uint32> **обязательный**. Количество товаров в ответе
- `nmIds` — array[integer<uint64>]. Список артикулов WB
- `offset` — integer<uint32> **обязательный**. После какого элемента выдавать данные
- `orderBy` — object **обязательный**. Параметры сортировки
  - `field` — string (avgPosition, openCard, addToCart, openToCart, orders, cartToOrder, visibility, minPrice, maxPrice) **обязательный**. Поле для сортировки: - `avgPosition` — по средней позиции - `addToCart` — по добавлениям в корзину - `openCard` — по открытию карточки (переход на страницу товара) - `orders` — по количеству заказов - `cartToOrder` — по конверсии в заказ из поиска - `openToCart` — по конверсии в корзину из поиска - `visibility` — по видимости товара - `minPrice` — по минимальной цене - `maxPrice` — по максимальной цене
  - `mode` — string (asc, desc) **обязательный**. Порядок сортировки: - `asc` — по возрастанию - `desc` — по убыванию
- `pastPeriod` — object. Прошлый период для сравнения. Количество дней — меньше или равно `currentPeriod`
  - `end` — string<date> **обязательный**. Дата окончания периода. Не позднее даты перед датой начала `currentPeriod`. Не ранее 365 суток от сегодня
  - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 365 суток от сегодня
- `positionCluster` — string (all, firstHundred, secondHundred, below) **обязательный**. Товары с какой средней позицией в поиске показывать в отчёте: - `all` — все - `firstHundred` — от 1 до 100 - `secondHundred` — от 101 до 200 - `below` — от 201 и ниже
- `subjectId` — integer<int32>. ID предмета
- `tagId` — integer<int64>. ID ярлыка

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
- `data` — object **обязательный**
  - `currency` — string **обязательный**. Валюта отчёта
  - `products` — array[object] **обязательный**. Список товаров в группе по фильтру
    - `addToCart` — object. Сколько раз товар из поиска добавили в корзину
      - `current` — integer **обязательный**. Текущее количество
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `avgPosition` — object. Средняя позиция товара в результатах поиска
      - `current` — integer **обязательный**. Текущая средняя позиция
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `brandName` — string. Бренд
    - `cartToOrder` — object. Конверсия в заказ из поиска — доля заказов товара по отношению ко всем добавлениям товара из поиска в корзину
      - `current` — integer **обязательный**. Текущая конверсия
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `feedbackRating` — number<float64>. Рейтинг по отзывам
    - `isAdvertised` — boolean. Находится ли товар в продвижении в Поисковой выдаче
    - `isCardRated` — boolean. Есть ли рейтинг у карточки товара
    - `isSubstitutedSKU` — boolean. Искали ли товар по подменному артикулу. Поле будет в ответе при наличии в запросе `includeSubstitutedSKUs` и/или `includeSearchTexts`
    - `mainPhoto` — string. URL главного фото карточки товара
    - `name` — string. Название товара
    - `nmId` — integer<int64>. Артикул WB
    - `openCard` — object. Количество переходов в карточку товара из поиска
      - `current` — integer **обязательный**. Текущее количество переходов
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `openToCart` — object. Конверсия в корзину из поиска — доля добавлений товара в корзину по отношению ко всем переходам в карточку товара из поиска
      - `current` — integer **обязательный**. Текущая конверсия
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `orders` — object. Сколько раз товары из поиска заказали
      - `current` — integer **обязательный**. Текущее количество
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %
    - `price` — object. Цена
      - `maxPrice` — integer<uint64> **обязательный**. Максимальная цена продавца со скидкой продавца (без учёта скидки WB Клуба)
      - `minPrice` — integer<uint64> **обязательный**. Минимальная цена продавца со скидкой продавца (без учёта скидки WB Клуба)
    - `rating` — number<float64>. Рейтинг карточки товара
    - `subjectName` — string. Название предмета
    - `vendorCode` — string. Артикул продавца
    - `visibility` — object. Процент видимости товара в результатах поиска
      - `current` — integer **обязательный**. Текущий процент видимости
      - `dynamics` — integer. Динамика по сравнению с предыдущим периодом, %

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
