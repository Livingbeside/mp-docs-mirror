---
title: Создать отчёт{{ /api/v2/nm-report/downloads }}
api: wb-analytics
method: POST
path: /api/v2/nm-report/downloads
operation_id: postV2NmReportDownloads
tags:
  - sellerAnalyticsCsv
spec_version: analytics
source: "https://dev.wildberries.ru/docs/openapi/analytics"
deprecated: false
content_sha: 6bbbe2e0affb3fae
---

# Создать отчёт{{ /api/v2/nm-report/downloads }}

`POST /api/v2/nm-report/downloads`

Описание метода Метод создаёт задание на генерацию отчёта с расширенной аналитикой продавца. Вы можете создать CSV-версии отчётов по [воронке продаж](./analytics#tag/salesFunnel) или [параметрам поиска](./analytics#tag/searchQueriesForYourItems) с группировкой по: * артикулам WB * предметам, брендам и ярлыкам В отчётах по воронке продаж можно группировать данные по дням, неделям или месяцам. Также можете создать CSV-версии отчётов по [текстам поисковых запросов](./analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportProductSearchTexts) и [остаткам](./analytics#tag/stocksReport). Каждый новый отчёт должен иметь уникальный ID. Не используйте одинаковые ID для разных отчётов — это может привести к ошибкам при генерации Набор параметров запроса в объекте `params` зависит от типа отчёта. Чтобы получить описание параметров, выберите тип отчёта в раскрывающемся списке в описании параметра `reportType`. Параметры `includeSubstitutedSKUs` и `includeSearchTexts` не могут одновременно иметь значение `false`. Если не удалось [получить отчёт](./analytics#tag/sellerAnalyticsCsv/operation/getV2NmReportDownloadsFileDownloadId), можно создать [повторное задание на генерацию](./analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloadsRetry). Также можно [получить список и проверить статусы](./analytics#tag/sellerAnalyticsCsv/operation/getV2NmReportDownloads) отчётов. Отчёты по остаткам — типы STOCK_HISTORY_REPORT_CSV и STOCK_HISTORY_DAILY_CSV — можно создать без подписки Джем Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 3 запроса | 20 сек | 3 запроса | | Сервисный | 1 мин | 3 запроса | 20 сек | 3 запроса | | Базовый с секретом | 1 мин | 3 запроса | 20 сек | 3 запроса | | Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `id` — string<uuid> **обязательный**. ID отчёта в UUID-формате. Генерируется продавцом самостоятельно
- `reportType` — string **обязательный**. Тип отчёта `DETAIL_HISTORY_REPORT` — Воронка продаж. По артикулам WB
- `userReportName` — string. Название отчёта. Если не указано, сформируется автоматически
- `params` — object **обязательный**. Параметры отчёта
  - `nmIDs` — array[integer<int64>]. Артикулы WB, по которым составить отчёт. Оставьте пустым, чтобы получить отчёт обо всех товарах
  - `subjectIds` — array[integer<int32>]. Список ID предметов для фильтрации
  - `brandNames` — array[string]. Список брендов для фильтрации
  - `tagIds` — array[integer<int64>]. Список ID ярлыков для фильтрации
  - `startDate` — string<date> **обязательный**. Начало периода
  - `endDate` — string<date> **обязательный**. Конец периода
  - `timezone` — string. Временная зона по формату [IANA](https://nodatime.org/TimeZones) По умолчанию: `Europe/Moscow`.
  - `aggregationLevel` — string (day, week, month). Как сгруппировать данные (по умолчанию по дням): * `day` — по дням * `week` — по неделям * `month` — по месяцам
  - `skipDeletedNm` — boolean. Скрыть удалённые товары
- `id` — string<uuid> **обязательный**. ID отчёта в UUID-формате. Генерируется продавцом самостоятельно
- `reportType` — string **обязательный**. Тип отчёта `GROUPED_HISTORY_REPORT` — Воронка продаж. По предметам, брендам и ярлыкам
- `userReportName` — string. Название отчёта. Если не указано, сформируется автоматически
- `params` — object **обязательный**. Параметры отчёта
  - `subjectIds` — array[integer<int32>]. Список ID предметов для фильтрации
  - `brandNames` — array[string]. Список брендов для фильтрации
  - `tagIds` — array[integer<int64>]. Список ID ярлыков для фильтрации
  - `startDate` — string<date> **обязательный**. Начало периода
  - `endDate` — string<date> **обязательный**. Конец периода
  - `timezone` — string. Временная зона по формату [IANA](https://nodatime.org/TimeZones) По умолчанию: `Europe/Moscow`.
  - `aggregationLevel` — string. Как сгруппировать данные (по умолчанию по дням): * `day` — по дням * `week` — по неделям * `month` — по месяцам
  - `skipDeletedNm` — boolean. Скрыть удалённые товары
- `id` — string<uuid> **обязательный**. ID отчёта в UUID-формате. Генерируется продавцом самостоятельно
- `reportType` — string **обязательный**. Тип отчёта `SEARCH_QUERIES_PREMIUM_REPORT_GROUP` — Отчёт по параметрам поиска. По предметам, брендам и ярлыкам
- `userReportName` — string. Название отчёта. Если не указано, сформируется автоматически
- `params` — object **обязательный**. Параметры отчёта
  - `currentPeriod` — object **обязательный**. Текущий период
    - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 365 суток от сегодня
    - `end` — string<date> **обязательный**. Дата окончания периода. Не ранее 365 суток от сегодня
  - `pastPeriod` — object. Прошлый период для сравнения. Количество дней — меньше или равно `currentPeriod`
    - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 365 суток от сегодня
    - `end` — string<date> **обязательный**. Дата окончания периода. Не позднее даты перед датой начала `currentPeriod`. Не ранее 365 суток от сегодня
  - `nmIds` — array[integer<int64>]. Артикулы WB, по которым составить отчёт. Оставьте пустым, чтобы получить отчёт обо всех товарах
  - `subjectIds` — array[integer<int32>] **обязательный**. Список ID предметов для фильтрации. Оставьте пустым, чтобы получить отчёт по всем предметам
  - `brandNames` — array[string]. Список брендов для фильтрации
  - `tagIds` — array[integer<int64>]. Список ID ярлыков для фильтрации
  - `orderBy` — object **обязательный**. Параметры сортировки
    - `field` — string (avgPosition, openCard, addToCart, openToCart, orders, cartToOrder, visibility) **обязательный**. Поле для сортировки: - `avgPosition` — по средней позиции - `addToCart` — по добавлениям в корзину - `openCard` — по открытию карточки (переход на страницу товара) - `orders` — по количеству заказов - `cartToOrder` — по конверсии в заказ из поиска - `openToCart` — по конверсии в корзину из поиска - `visibility` — по видимости товара
    - `mode` — string (asc, desc) **обязательный**. Порядок сортировки: - `asc` — по возрастанию - `desc` — по убыванию
  - `positionCluster` — string (all, firstHundred, secondHundred, below) **обязательный**. Товары с какой средней позицией в поиске показывать в отчёте: - `all` — все - `firstHundred` — от 1 до 100 - `secondHundred` — от 101 до 200 - `below` — от 201 и ниже
  - `includeSubstitutedSKUs` — boolean. Показать данные по прямым запросам с [подменным артикулом](https://seller.wildberries.ru/help-center/article/A-524) По умолчанию: `True`.
  - `includeSearchTexts` — boolean. Показать данные по поисковым запросам без учёта подменного артикула По умолчанию: `True`.
- `id` — string<uuid> **обязательный**. ID отчёта в UUID-формате. Генерируется продавцом самостоятельно
- `reportType` — string **обязательный**. Тип отчёта `SEARCH_QUERIES_PREMIUM_REPORT_PRODUCT` — Отчёт по параметрам поиска. По артикулам WB
- `userReportName` — string. Название отчёта. Если не указано, сформируется автоматически
- `params` — object **обязательный**. Параметры отчёта
  - `currentPeriod` — object **обязательный**. Текущий период
    - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 365 суток от сегодня
    - `end` — string<date> **обязательный**. Дата окончания периода. Не ранее 365 суток от сегодня
  - `pastPeriod` — object. Прошлый период для сравнения. Количество дней — меньше или равно `currentPeriod`
    - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 365 суток от сегодня
    - `end` — string<date> **обязательный**. Дата окончания периода. Не позднее даты перед датой начала `currentPeriod`. Не ранее 365 суток от сегодня
  - `subjectId` — integer<int32>. ID предмета. Используйте значение `0`, чтобы получить отчёт по всем предметам
  - `brandName` — string. Бренд
  - `tagId` — integer<int64>. ID ярлыка. Чтобы получить отчёт по всем ярлыкам, укажите значение 0
  - `nmIds` — array[integer<int64>]. Артикулы WB, по которым составить отчёт. Оставьте пустым, чтобы получить отчёт обо всех товарах
  - `positionCluster` — string (all, firstHundred, secondHundred, below) **обязательный**. Товары с какой средней позицией в поиске показывать в отчёте: - `all` — все - `firstHundred` — от 1 до 100 - `secondHundred` — от 101 до 200 - `below` — от 201 и ниже
  - `orderBy` — object **обязательный**. Параметры сортировки
    - `field` — string (openCard, addToCart, orderCount, orderSum, buyoutCount, buyoutSum, cancelCount, cancelSum, avgPrice, stockMpQty, stockWbQty, shareOrderPercent…) **обязательный**. Поле для сортировки: - `openCard` — Перешли в карточку - `addToCart` — Положили в корзину - `orderCount` — Заказали товаров, шт - `orderSum` — Заказали на сумму - `buyoutCount` — Выкупили товаров, шт - `buyoutSum` — Выкупили на сумму - `cancelCount` — Отменили и вернули товаров, шт - `cancelSum` — Отменили и вернули на сумму - `avgPrice` — Средняя цена - `stockMpQty` — Остатки на складах продавца, шт - `stockWbQty` — Остатки на складах WB, шт - `shareOrderPercent` — Доля в выручке - `addToWishlist` — Добавили в **Отложенные** - `timeToReady` — Среднее время доставки - `localizationPercent` — Локальные заказы в рамках одного региона - `wbClub.orderCount` — Заказали товаров с WB Клубом, шт - `wbClub.orderSum` — Заказали с WB Клубом на сумму - `wbClub.buyoutSum` — Выкупили товаров с WB Клубом, шт - `wbClub.buyoutCount` — Процент выкупа с WB Клубом - `wbClub.cancelSum` — Отменили и вернули товаров с WB Клубом на сумму - `wbClub.avgPrice` — Средняя цена с WB Клубом - `wbClub.buyoutPercent` — Процент выкупа с WB Клубом - `wbClub.avgOrderCountPerDay` — Среднее количество заказов в день с WB Клубом, шт - `wbClub.cancelCount` — Отменили и вернули товаров с WB Клубом, шт По умолчанию: `openCard`.
    - `mode` — string (asc, desc) **обязательный**. Порядок сортировки: - `asc` — по возрастанию - `desc` — по убыванию По умолчанию: `desc`.
  - `includeSubstitutedSKUs` — boolean. Показать данные по прямым запросам с [подменным артикулом](https://seller.wildberries.ru/help-center/article/A-524) По умолчанию: `True`.
  - `includeSearchTexts` — boolean. Показать данные по поисковым запросам без учёта подменного артикула По умолчанию: `True`.
- `id` — string<uuid> **обязательный**. ID отчёта в UUID-формате. Генерируется продавцом самостоятельно
- `reportType` — string **обязательный**. Тип отчёта `SEARCH_QUERIES_PREMIUM_REPORT_TEXT` — Отчёт по текстам поисковых запросов
- `userReportName` — string. Название отчёта. Если не указано, сформируется автоматически
- `params` — object **обязательный**. Параметры отчёта
  - `currentPeriod` — object **обязательный**. Текущий период
    - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 365 суток от сегодня
    - `end` — string<date> **обязательный**. Дата окончания периода. Не ранее 365 суток от сегодня
  - `pastPeriod` — object. Прошлый период для сравнения. Количество дней — меньше или равно `currentPeriod`
    - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 365 суток от сегодня
    - `end` — string<date> **обязательный**. Дата окончания периода. Не позднее даты перед датой начала `currentPeriod`. Не ранее 365 суток от сегодня
  - `nmIds` — array[?]. Артикулы WB, по которым составить отчёт. Оставьте пустым, чтобы получить отчёт по всем товарам
  - `subjectIds` — array[integer<int32>]. Список ID предметов для фильтрации
  - `brandNames` — array[string]. Список брендов для фильтрации
  - `tagIds` — array[integer<int64>]. Список ID ярлыков для фильтрации
  - `topOrderBy` — string (openCard, addToCart, openToCart, orders, cartToOrder) **обязательный**. Фильтрация по поисковым запросам, по которым больше всего: - `openCard` — перешли в карточку - `addToCart` — добавили в корзину - `openToCart` — конверсия в корзину - `orders` — заказали товаров - `cartToOrder` — конверсия в заказ
  - `orderBy` — object **обязательный**. Параметры сортировки
    - `field` — string (avgPosition, openCard, addToCart, openToCart, orders, cartToOrder, visibility) **обязательный**. Поле для сортировки: - `avgPosition` — по средней позиции - `addToCart` — по добавлениям в корзину - `openCard` — по открытию карточки (переход на страницу товара) - `orders` — по количеству заказов - `cartToOrder` — по конверсии в заказ из поиска - `openToCart` — по конверсии в корзину из поиска - `visibility` — по видимости товара
    - `mode` — string (asc, desc) **обязательный**. Порядок сортировки: - `asc` — по возрастанию - `desc` — по убыванию
  - `includeSubstitutedSKUs` — boolean. Показать данные по прямым запросам с [подменным артикулом](https://seller.wildberries.ru/help-center/article/A-524) По умолчанию: `True`.
  - `includeSearchTexts` — boolean. Показать данные по поисковым запросам без учёта подменного артикула По умолчанию: `True`.
  - `limit` — integer<uint64> **обязательный**
- `id` — string<uuid> **обязательный**. ID отчёта в UUID-формате. Генерируется продавцом самостоятельно
- `reportType` — string **обязательный**. Тип отчёта `STOCK_HISTORY_REPORT_CSV` — Отчёт по статистике остатков
- `userReportName` — string. Название отчёта. Если не указано, сформируется автоматически
- `params` — object **обязательный**. Параметры отчёта
  - `nmIDs` — array[integer<int64>]. Список артикулов WB для фильтрации
  - `subjectIDs` — array[integer<int32>]. Список ID предметов для фильтрации
  - `brandNames` — array[string]. Список брендов для фильтрации
  - `tagIDs` — array[integer<int64>]. Список ID ярлыков для фильтрации
  - `currentPeriod` — object **обязательный**. Период
    - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 3 месяцев от текущей даты
    - `end` — string<date> **обязательный**. Дата окончания периода. Не ранее 3 месяцев от текущей даты
  - `stockType` — string (, wb, mp) **обязательный**. Тип складов хранения товаров: - `""` — все - `wb` — склады WB - `mp` — склады продавца
  - `skipDeletedNm` — boolean **обязательный**. Скрыть удалённые товары
  - `availabilityFilters` — array[string (deficient, actual, balanced, nonActual, nonLiquid, invalidData)] **обязательный**. Доступность товара: - `deficient` — Дефицит - `actual` — Актуальный - `balanced` — Баланс - `nonActual` — Неактуальный - `nonLiquid` — Неликвид - `invalidData` — Не рассчитано
  - `orderBy` — object **обязательный**. Вид сортировки данных
    - `field` — string (ordersCount, ordersSum, avgOrders, buyoutCount, buyoutSum, buyoutPercent, stockCount, stockSum, saleRate, avgStockTurnover, toClientCount, fromClientCount…) **обязательный**. Сортировка по полю: - `ordersCount` — Заказы, шт. - `ordersSum` — Заказы, сумма - `avgOrders` — Среднее количество заказов в день - `buyoutCount` — Выкупы, шт. - `buyoutSum` — Выкупы, сумма - `buyoutPercent` — Процент выкупа - `stockCount` — Остатки на текущий день, шт. - `stockSum` — Стоимость остатков на текущий день - `saleRate` — Оборачиваемость текущих остатков - `avgStockTurnover` — Оборачиваемость средних остатков - `toClientCount` — В пути к клиенту, шт. - `fromClientCount` — В пути от клиента, шт. - `minPrice` — Минимальная цена продавца со скидкой продавца (без учёта скидки WB Клуба) - `maxPrice` — Максимальная цена продавца со скидкой продавца (без учёта скидки WB Клуба) - `officeMissingTime` — Время отсутствия товара на складе - `lostOrdersCount` — Упущенные заказы, шт. - `lostOrdersSum` — Упущенные заказы, сумма - `lostBuyoutsCount` — Упущенные выкупы, шт. - `lostBuyoutsSum` — Упущенные выкупы, сумма
    - `mode` — string (asc, desc) **обязательный**. Порядок сортировки: - asc — по возрастанию - desc — по убыванию
- `id` — string<uuid> **обязательный**. ID отчёта в UUID-формате. Генерируется продавцом самостоятельно
- `reportType` — string **обязательный**. Тип отчёта `STOCK_HISTORY_DAILY_CSV` — Отчёт по истории остатков
- `userReportName` — string. Название отчёта. Если не указано, сформируется автоматически
- `params` — object **обязательный**. Параметры отчёта
  - `nmIds` — array[integer<int64>]. Список артикулов WB для фильтрации
  - `subjectIds` — array[integer<int32>]. Список ID предметов для фильтрации
  - `brandNames` — array[string]. Список брендов для фильтрации
  - `tagIds` — array[integer<int64>]. Список ID ярлыков для фильтрации
  - `currentPeriod` — object **обязательный**. Период
    - `start` — string<date> **обязательный**. Дата начала периода. Не позднее `end`. Не ранее 3 месяцев от текущей даты
    - `end` — string<date> **обязательный**. Дата окончания периода. Не ранее 3 месяцев от текущей даты
  - `stockType` — string (, wb, mp) **обязательный**. Тип складов хранения товаров: - `""` — все - `wb` — склады WB - `mp` — склады продавца
  - `skipDeletedNm` — boolean **обязательный**. Скрыть удалённые товары

## Ответы

**200** — Успешно

- `data` — string **обязательный**. Уведомление, что началась генерация отчёта

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

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string **обязательный**. Детали ошибки
- `requestId` — string **обязательный**. Уникальный ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB
