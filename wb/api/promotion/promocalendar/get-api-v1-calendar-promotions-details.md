---
title: Детальная информация об акциях{{ /api/v1/calendar/promotions/details }}
api: wb-promotion
method: GET
path: /api/v1/calendar/promotions/details
operation_id: getV1CalendarPromotionsDetails
tags:
  - promoCalendar
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 63bd45327fac55c9
---

# Детальная информация об акциях{{ /api/v1/calendar/promotions/details }}

`GET /api/v1/calendar/promotions/details`

Описание метода Метод возвращает подробную информацию об [акции](./promotion#tag/promoCalendar/operation/getV1CalendarPromotionsDetails) по ID. Лимит запросов на один аккаунт продавца для всех методов категории Календарь акций : | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов | | Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов | | Базовый с секретом | 6 сек | 10 запросов | 600 мс | 5 запросов | | Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `promotionIDs` | query | array[integer] | да | ID акций, по которым нужно вернуть информацию |

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `promotions` — array[object]. Список акций
    - `id` — integer. ID акции
    - `name` — string. Название акции
    - `description` — string. Описание акции
    - `advantages` — array[string]. Преимущества акции
    - `startDateTime` — string. Начало акции
    - `endDateTime` — string. Конец акции
    - `inPromoActionLeftovers` — integer. Количество товаров с остатками, участвующих в акции
    - `inPromoActionTotal` — integer. Общее количество товаров, участвующих в акции
    - `notInPromoActionLeftovers` — integer. Количество товаров с остатками, не участвующих в акции
    - `notInPromoActionTotal` — integer. Общее количество товаров, не участвующих в акции
    - `participationPercentage` — integer. Уже участвующие в акции товары, %. Рассчитывается по товарам в акции и с остатком
    - `type` — string (regular, auto). Тип акции: - `regular` — акция - `auto` — автоакция
    - `exceptionProductsCount` — integer<uint>. Количество товаров, исключенных из автоакции до её старта. Только при `"type": "auto"`. В момент старта акции эти товары автоматически будут без скидки
    - `ranging` — array[object]. Ранжирование (если подключено)
      - `condition` — string. Тип [ранжирования](https://seller.wildberries.ru/help-center/article/A-385): - `productsInPromotion` — продвижение получат товары продавца, участвующие в акции - `calculateProducts` — продвижение получат любые товара продавца, предложенные к участию в акции - `allProducts` — продвижение получат все товары продавца
      - `participationRate` — integer<uint>. Количество товаров продавца для перехода на следующий уровень ранжирования, %
      - `boost` — integer<uint>. Текущий уровень поднятия в поиске, %

**400** — Неправильный запрос

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
