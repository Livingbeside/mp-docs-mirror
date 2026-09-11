---
title: Список товаров в черновике{{ /api/supplies/v1/drafts/{draftId}/items }}
api: wb-orders-fbw
method: GET
path: /api/supplies/v1/drafts/{draftId}/items
operation_id: getV1DraftsDraftIdItems
tags:
  - supplyDrafts
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: 55350cbbd8059a9c
---

# Список товаров в черновике{{ /api/supplies/v1/drafts/{draftId}/items }}

`GET /api/supplies/v1/drafts/{draftId}/items`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену

Метод возвращает список товаров черновика.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 30 запросов | 2 сек | 10 запросов |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `draftId` | path | string | да | ID черновика |

## Ответы

**200** — Успешно

- `skuQuantity` — integer **обязательный**. Количество баркодов
- `itemQuantity` — integer **обязательный**. Количество единиц товара
- `items` — array[object] **обязательный**. Список товаров
  - `sku` — string **обязательный**. Баркод
  - `color` — string **обязательный**. Цвет товара
  - `quantity` — integer **обязательный**. Количество единиц товара
  - `brandName` — string **обязательный**. Бренд
  - `imgSrc` — string **обязательный**. Ссылка на изображение товара
  - `nmId` — integer **обязательный**. Артикул WB
  - `subjectName` — string **обязательный**. Предмет
  - `techSize` — string **обязательный**. Размер товара
  - `title` — string **обязательный**. Название товара
  - `vendorCode` — string **обязательный**. Артикул продавца

**400** — Неправильный запрос

- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string. Детали ошибки
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

**404** — Не найдено

- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string. Детали ошибки
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
