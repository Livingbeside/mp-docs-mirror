---
title: Лимиты карточек товаров{{ /content/v2/cards/limits }}
api: wb-work-with-products
method: GET
path: /content/v2/cards/limits
operation_id: get-content-v2-cards-limits
tags:
  - listingItems
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: a406b4e2ac0f324b
---

# Лимиты карточек товаров{{ /content/v2/cards/limits }}

`GET /content/v2/cards/limits`

Описание метода Возвращает бесплатные и платные лимиты продавца на [создание карточек товаров](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload/post). Формула для получения количества карточек, которые можно создать: > (`freeLimits` + `paidLimits`) - количество созданных карточек Созданными считаются карточки, которые можно получить через методы [список карточек товаров](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1list/post) и [список карточек товаров в корзине](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1trash/post). Лимит запросов на один аккаунт продавца для методов: получения лимитов карточек товаров получения несозданных карточек товаров с ошибками | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 100 запросов | 600 мс | 5 запросов | | Сервисный | 1 мин | 100 запросов | 600 мс | 5 запросов | | Базовый с секретом | 1 мин | 100 запросов | 600 мс | 5 запросов | | Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос | В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента .

## Ответы

**200** — Успешно

- `data` — object
  - `freeLimits` — integer. Количество бесплатных лимитов
  - `paidLimits` — integer. Количество оплаченных лимитов
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки
- `additionalErrors` — string. Дополнительные ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**403** — Доступ запрещён

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки
- `additionalErrors` — string. Дополнительные ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
