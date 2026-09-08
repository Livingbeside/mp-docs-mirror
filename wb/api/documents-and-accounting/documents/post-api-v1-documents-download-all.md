---
title: Получить документы
api: wb-documents-and-accounting
method: POST
path: /api/v1/documents/download/all
operation_id: postV1DocumentsDownloadAll
tags:
  - documents
spec_version: finances
source: "https://dev.wildberries.ru/docs/openapi/documents-and-accounting"
deprecated: false
content_sha: 3a491824b71c08b3
---

# Получить документы

`POST /api/v1/documents/download/all`

Описание метода

Метод загружает несколько документов из [списка документов продавца](./financial-reports-and-accounting#tag/documents/operation/getV1DocumentsList).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 5 мин | 1 запрос | 5 мин | 5 запросов |
| Сервисный | 5 мин | 1 запрос | 5 мин | 5 запросов |
| Базовый с секретом | 5 мин | 1 запрос | 5 мин | 5 запросов |
| Базовый | 24 ч | 1 запрос | 24 ч | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `params` — array[object]
  - `extension` — string. Формат документа
  - `serviceName` — string. Уникальный ID документа

## Ответы

**200** — Успешно

- `data` — object
  - `fileName` — string. Название документа
  - `extension` — string. Формат документа
  - `document` — string. Документ в кодировке base64

**400** — Неправильный запрос

- `title` — string. Заголовок ошибки
- `status` — number. HTTP статус-код
- `detail` — string. Детализация ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB

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
