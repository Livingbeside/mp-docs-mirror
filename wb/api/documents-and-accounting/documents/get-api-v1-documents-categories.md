---
title: Категории документов
api: wb-documents-and-accounting
method: GET
path: /api/v1/documents/categories
operation_id: getV1DocumentsCategories
tags:
  - documents
spec_version: finances
source: "https://dev.wildberries.ru/docs/openapi/documents-and-accounting"
deprecated: false
content_sha: 05b16d9ee2e30aba
---

# Категории документов

`GET /api/v1/documents/categories`

Описание метода

Метод возвращает категории документов для получения [списка документов продавца](./documents-and-accounting#tag/documents/operation/getV1DocumentsList).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 10 сек | 1 запрос | 10 сек | 5 запросов |
| Сервисный | 10 сек | 1 запрос | 10 сек | 5 запросов |
| Базовый с секретом | 10 сек | 1 запрос | 10 сек | 5 запросов |
| Базовый | 24 ч | 1 запрос | 24 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `locale` | query | string | нет | Язык поля `title`: - `ru` — русский - `en` — английский - `zh` — китайский |

## Ответы

**200** — Успешно

- `data` — object
  - `categories` — array[object]. Категории документов
    - `name` — string. ID категории документа из параметра [запроса](./documents-and-accounting#tag/documents/operation/getV1DocumentsList) `category`
    - `title` — string. Название категории документа из поля [ответа](./documents-and-accounting#tag/documents/operation/getV1DocumentsList) `category`

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
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
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
