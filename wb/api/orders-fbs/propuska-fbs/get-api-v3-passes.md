---
title: Получить список пропусков
api: wb-orders-fbs
method: GET
path: /api/v3/passes
operation_id: get-api-v3-passes
tags:
  - Пропуска FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 30addc796685348c
---

# Получить список пропусков

`GET /api/v3/passes`

Описание метода

Метод возвращает список всех [созданных](./orders-fbs#tag/Propuska-FBS/paths/~1api~1v3~1passes/post) пропусков продавца.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Ответы

**200** — Успешно

- `carModel` — string. Марка машины
- `carNumber` — string. Номер машины
- `dateEnd` — string. Дата окончания действия пропуска
- `firstName` — string. Имя водителя
- `id` — integer<int64>. ID пропуска
- `lastName` — string. Фамилия водителя
- `officeAddress` — string. Адрес склада
- `officeId` — integer<int64>. ID склада
- `officeName` — string. Название склада

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
