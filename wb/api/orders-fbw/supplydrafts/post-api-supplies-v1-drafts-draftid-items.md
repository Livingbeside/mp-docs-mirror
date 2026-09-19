---
title: Добавить товары в черновик{{ /api/supplies/v1/drafts/{draftId}/items }}
api: wb-orders-fbw
method: POST
path: /api/supplies/v1/drafts/{draftId}/items
operation_id: postV1DraftsDraftIdItems
tags:
  - supplyDrafts
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: ac9835b5fa9db939
---

# Добавить товары в черновик{{ /api/supplies/v1/drafts/{draftId}/items }}

`POST /api/supplies/v1/drafts/{draftId}/items`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену

Метод добавляет товары в черновик поставки.

 Метод работает по принципу атомарности:
 - если все баркоды прошли валидацию успешно, то все товары добавятся в черновик. В ответе вернётся {"results":[]}
 - если хотя бы один баркод не прошел валидацию, ни один товар в черновик не добавится. В ответе вернётся список невалидных баркодов

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 30 запросов | 2 сек | 10 запросов |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `draftId` | path | string | да | ID черновика |

## Запрос

**Тело запроса** (`application/json`):

- `items` — array[object] **обязательный**. Список товаров
  - `quantity` — integer **обязательный**. Количество единиц товара
  - `sku` — string **обязательный**. Баркод из карточки товара

## Ответы

**200** — Успешно

- `results` — array[object] **обязательный**. Список невалидных баркодов с ошибками
  - `error` — object **обязательный**. Детали ошибки
    - `detail` — string **обязательный**. Детали ошибки
    - `title` — string **обязательный**. Заголовок ошибки
  - `sku` — string **обязательный**. Баркод

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

**403** — Доступ запрещён

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
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
