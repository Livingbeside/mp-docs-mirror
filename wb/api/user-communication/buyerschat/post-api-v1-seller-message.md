---
title: Отправить сообщение
api: wb-user-communication
method: POST
path: /api/v1/seller/message
operation_id: postV1SellerMessage
tags:
  - buyersChat
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: 03d97c2fe49b777b
---

# Отправить сообщение

`POST /api/v1/seller/message`

Описание метода

Метод отправляет сообщения в [чат с покупателем](./user-communication#tag/buyersChat/operation/getV1SellerChats).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Сервисный | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Базовый с секретом | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Запрос

**Тело запроса** (`multipart/form-data`):

- `file` — array[string<binary>]. Файлы, формат JPEG, PDF или PNG, максимальный размер — 5 Мб каждый. Максимальный суммарный размер файлов — 30 Мб.
- `message` — string. Текст сообщения. Максимум 1000 символов.
- `replySign` — string **обязательный**. Подпись чата. Можно получить из [информации по чату](./user-communication#tag/buyersChat/operation/getV1SellerChats) или [данных события](./user-communication#tag/buyersChat/operation/getV1SellerEvents), если в событии есть поле `"isNewChat": true`.

## Ответы

**200** — Успешно

- `errors` — array[string]. Ошибки загрузки файлов, если есть
- `result` — object
  - `addTime` — integer<Unix Timestamp в миллисекундах>. Дата и время создания чата
  - `chatID` — string. ID чата
  - `sign` — string. Подпись чата

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
