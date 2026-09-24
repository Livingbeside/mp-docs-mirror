---
title: Лимиты карточек товаров
api: wb-item-management
method: GET
path: /content/v2/cards/limits
operation_id: getV2CardsLimits
tags:
  - listingItems
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: b490d7d3eab3d4f8
---

# Лимиты карточек товаров

`GET /content/v2/cards/limits`

Описание метода

Возвращает бесплатные и платные лимиты продавца на [создание карточек товаров](./item-management#tag/listingItems/operation/postV2CardsUpload).

Формула для получения количества карточек, которые можно создать:

> (`freeLimits` + `paidLimits`) - количество созданных карточек

Созданными считаются карточки, которые можно получить через методы [список карточек товаров](./item-management#tag/listings/operation/postV2GetCardsList) и [список карточек товаров в корзине](./item-management#tag/listings/operation/postV2GetCardsTrash).

Лимит запросов на один аккаунт продавца для методов:

 [получения лимитов карточек товаров](./item-management#tag/listingItems/operation/getV2CardsLimits)

 [получения несозданных карточек товаров с ошибками](./item-management#tag/listings/operation/postV2CardsErrorList)

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Сервисный | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

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
- `errorText` — string. Описание ошибки
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
