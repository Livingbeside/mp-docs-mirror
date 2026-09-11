---
title: Список черновиков
api: wb-orders-fbw
method: GET
path: /api/supplies/v1/drafts
operation_id: getV1Drafts
tags:
  - supplyDrafts
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: 5c1c136fc2604cc7
---

# Список черновиков

`GET /api/supplies/v1/drafts`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену

Метод возвращает список черновиков поставок.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 30 запросов | 2 сек | 10 запросов |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `limit` | query | integer | нет | Количество черновиков в ответе |
| `offset` | query | integer | нет | Сколько элементов пропустить. Например, для значения 10 ответ начнется с 11 элемента |
| `sort` | query | string (createDt, updateDt) | нет | Сортировка: - `createdDt` — по дате создания черновика - `updatedDt` — по дате обновления черновика |
| `order` | query | string (asc, desc) | нет | Порядок выдачи: - `desc` — по убыванию - `asc` — по возрастанию |

## Ответы

**200** — Успешно

- `total` — integer **обязательный**. Общее количество черновиков
- `drafts` — array[object] **обязательный**. Список черновиков
  - `draftId` — string **обязательный**. ID черновика
  - `phone` — string **обязательный**. Телефон пользователя, создавшего черновик
  - `createdAt` — string<ISO 8601> **обязательный**. Дата и время создания черновика
  - `updatedAt` — string<ISO 8601> **обязательный**. Дата и время последнего обновления черновика
  - `skuQuantity` — integer **обязательный**. Количество баркодов
  - `itemQuantity` — integer **обязательный**. Количество единиц товара

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
