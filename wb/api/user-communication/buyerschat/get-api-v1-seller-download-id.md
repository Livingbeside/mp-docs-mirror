---
title: Получить файл из сообщения{{ /api/v1/seller/download/{id} }}
api: wb-user-communication
method: GET
path: /api/v1/seller/download/{id}
operation_id: getV1SellerDownloadId
tags:
  - buyersChat
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: 4bb426add3219a4d
---

# Получить файл из сообщения{{ /api/v1/seller/download/{id} }}

`GET /api/v1/seller/download/{id}`

Описание метода

Метод возвращает файл или изображение из сообщения по его ID.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Сервисный | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Базовый с секретом | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Базовый | 1 ч | 10 запросов | 6 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `id` | path | string | да | ID файла, см. значение поля `downloadID` в методе [События чатов](./user-communication#tag/buyersChat/operation/getV1SellerEvents) |

## Ответы

**200** — Успешно

**202** — Файл на модерации

- `moderationState` — string **обязательный**. Статус модерации
- `retrySeconds` — integer **обязательный**. Секунд до следующей попытки запроса файла

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `error` — string. Текст ошибки
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

**451** — Файл не прошёл модерацию

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. ID запроса
- `status` — integer. HTTP статус-код
- `title` — string. Заголовок ошибки
