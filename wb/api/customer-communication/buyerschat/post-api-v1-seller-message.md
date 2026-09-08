---
title: Отправить сообщение
api: wb-customer-communication
method: POST
path: /api/v1/seller/message
operation_id: postV1SellerMessage
tags:
  - buyersChat
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
deprecated: false
content_sha: eb7bdc6bc97cb9f7
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

- `replySign` — string **обязательный**. Подпись чата. Можно получить из [информации по чату](./user-communication#tag/buyersChat/operation/getV1SellerChats) или [данных события](./user-communication#tag/buyersChat/operation/getV1SellerEvents), если в событии есть поле `"isNewChat": true`.
- `message` — string. Текст сообщения. Максимум 1000 символов.
- `file` — array[string<binary>]. Файлы, формат JPEG, PDF или PNG, максимальный размер — 5 Мб каждый. Максимальный суммарный размер файлов — 30 Мб.

## Ответы

**200** — Успешно

- `errors` — array[string]. Ошибки загрузки файлов, если есть
- `result` — object
  - `addTime` — integer<Unix Timestamp в миллисекундах>. Дата и время создания чата
  - `chatID` — string. ID чата
  - `sign` — string. Подпись чата

**400** — Неправильный запрос

- `status` — number. HTTP статус-код
- `title` — string. Заголовок ошибки
- `origin` — string. ID внутреннего сервиса WB
- `detail` — string. Детали ошибки
- `requestId` — string. Уникальный ID запроса
- `error` — string. Текст ошибки

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
