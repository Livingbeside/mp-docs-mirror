---
title: Детальная информация об акциях
api: wb-promotion
method: GET
path: /api/v1/calendar/promotions/details
operation_id: getV1CalendarPromotionsDetails
tags:
  - promoCalendar
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 4b3adf4b2a0e45a0
---

# Детальная информация об акциях

`GET /api/v1/calendar/promotions/details`

Описание метода

Метод возвращает подробную информацию об [акции](./promotion#tag/promoCalendar/operation/getV1CalendarPromotionsDetails) по ID.

Лимит запросов на один аккаунт продавца для всех методов категории Календарь акций:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `promotionIDs` | query | array[integer] | да | ID акций, по которым нужно вернуть информацию |

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `promotions` — array[object]. Список акций
    - `advantages` — array[string]. Преимущества акции
    - `description` — string. Описание акции
    - `endDateTime` — string. Конец акции
    - `exceptionProductsCount` — integer<uint>. Количество товаров, исключенных из автоакции до её старта. Только при `"type": "auto"`. В момент старта акции эти товары автоматически будут без скидки
    - `id` — integer. ID акции
    - `inPromoActionLeftovers` — integer. Количество товаров с остатками, участвующих в акции
    - `inPromoActionTotal` — integer. Общее количество товаров, участвующих в акции
    - `name` — string. Название акции
    - `notInPromoActionLeftovers` — integer. Количество товаров с остатками, не участвующих в акции
    - `notInPromoActionTotal` — integer. Общее количество товаров, не участвующих в акции
    - `participationPercentage` — integer. Уже участвующие в акции товары, %. Рассчитывается по товарам в акции и с остатком
    - `ranging` — array[object]. Ранжирование (если подключено)
      - `boost` — integer<uint>. Текущий уровень поднятия в поиске, %
      - `condition` — string. Тип [ранжирования](https://seller.wildberries.ru/help-center/article/A-385): - `productsInPromotion` — продвижение получат товары продавца, участвующие в акции - `calculateProducts` — продвижение получат любые товара продавца, предложенные к участию в акции - `allProducts` — продвижение получат все товары продавца
      - `participationRate` — integer<uint>. Количество товаров продавца для перехода на следующий уровень ранжирования, %
    - `startDateTime` — string. Начало акции
    - `type` — string (regular, auto). Тип акции: - `regular` — акция - `auto` — автоакция

**400** — Неправильный запрос

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
