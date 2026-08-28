---
title: Получить список пропусков{{ /api/v3/passes }}
api: wb-orders-fbs
method: GET
path: /api/v3/passes
operation_id: get-api-v3-passes
tags:
  - Пропуска FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 7fa5bc3942682515
---

# Получить список пропусков{{ /api/v3/passes }}

`GET /api/v3/passes`

Описание метода Метод возвращает список всех [созданных](./orders-fbs#tag/Propuska-FBS/paths/~1api~1v3~1passes/post) пропусков продавца. Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса .

## Ответы

**200** — Успешно

- `firstName` — string. Имя водителя
- `dateEnd` — string. Дата окончания действия пропуска
- `lastName` — string. Фамилия водителя
- `carModel` — string. Марка машины
- `carNumber` — string. Номер машины
- `officeName` — string. Название склада
- `officeAddress` — string. Адрес склада
- `officeId` — integer<int64>. ID склада
- `id` — integer<int64>. ID пропуска

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

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
