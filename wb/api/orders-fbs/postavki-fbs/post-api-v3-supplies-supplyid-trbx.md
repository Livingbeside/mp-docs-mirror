---
title: Добавить грузоместа к поставке{{ /api/v3/supplies/{supplyId}/trbx }}
api: wb-orders-fbs
method: POST
path: /api/v3/supplies/{supplyId}/trbx
operation_id: post-api-v3-supplies-supplyid-trbx
tags:
  - Поставки FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 6fa40ddda3940e4d
---

# Добавить грузоместа к поставке{{ /api/v3/supplies/{supplyId}/trbx }}

`POST /api/v3/supplies/{supplyId}/trbx`

Описание метода

Метод добавляет требуемое количество [грузомест](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D~1trbx/get) в [поставку](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D/get).

Грузоместа необходимо добавлять только в поставки, отгружаемые на ПВЗ.

Грузоместа можно добавить только в открытую поставку. Вы можете добавить столько же грузомест, сколько всего товаров в поставке, плюс ещё один.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `supplyId` | path | string | да | ID поставки |

## Запрос

**Тело запроса** (`application/json`):

- `amount` — integer **обязательный**. Количество грузомест, которые необходимо добавить к поставке

## Ответы

**201** — Создано

- `trbxIds` — array[string]. Список ID грузомест, которые были созданы

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
