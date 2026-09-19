---
title: Удалить товары из черновика{{ /api/supplies/v1/drafts/{draftId}/items }}
api: wb-orders-fbw
method: DELETE
path: /api/supplies/v1/drafts/{draftId}/items
operation_id: deleteV1DraftsDraftIdItems
tags:
  - supplyDrafts
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: f9e03f92e3aa9abe
---

# Удалить товары из черновика{{ /api/supplies/v1/drafts/{draftId}/items }}

`DELETE /api/supplies/v1/drafts/{draftId}/items`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену

Метод удаляет товары из черновика поставки по списку баркодов.

 
 Баркоды не валидируются. Если в запросе вы передали некорректные баркоды, вы не получите ошибку. При этом корректные баркоды будут удалены из черновика.
 

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

- `skus` — array[string] **обязательный**. Список баркодов

## Ответы

**200** — Успешно

- `results` — array[?] **обязательный**

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
