---
title: Создать пропуск
api: wb-orders-fbs
method: POST
path: /api/v3/passes
operation_id: post-api-v3-passes
tags:
  - Пропуска FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: fecfe2d378d25acf
---

# Создать пропуск

`POST /api/v3/passes`

Описание метода

Метод создаёт [пропуск продавца](./orders-fbs#tag/Propuska-FBS/paths/~1api~1v3~1passes/get) с привязкой к складу WB.

Пропуск действует 48 часов со времени создания.

 Максимум 1 запрос в 10 минут на один аккаунт продавца.

 Один запрос с кодами ответов 4XX учитывается как 10 запросов.

 

 В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `carModel` — string **обязательный**. Марка машины
- `carNumber` — string **обязательный**. Номер машины
- `firstName` — string **обязательный**. Имя водителя
- `lastName` — string **обязательный**. Фамилия водителя
- `officeId` — integer<int64> **обязательный**. ID склада

## Ответы

**201** — Создано

- `id` — integer. ID пропуска продавца

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

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

**403** — Доступ запрещён

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**404** — Не найдено

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
