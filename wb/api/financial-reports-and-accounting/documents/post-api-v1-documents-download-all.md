---
title: Получить документы
api: wb-financial-reports-and-accounting
method: POST
path: /api/v1/documents/download/all
operation_id: postV1DocumentsDownloadAll
tags:
  - documents
spec_version: finances
source: "https://dev.wildberries.ru/docs/openapi/financial-reports-and-accounting"
deprecated: false
content_sha: 2d03795941825d46
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
  - `document` — string. Документ в кодировке base64
  - `extension` — string. Формат документа
  - `fileName` — string. Название документа

**400** — Неправильный запрос

- `detail` — string. Детализация ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `title` — string. Заголовок ошибки

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
