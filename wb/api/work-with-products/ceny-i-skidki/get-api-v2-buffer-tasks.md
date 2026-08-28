---
title: Состояние необработанной загрузки{{ /api/v2/buffer/tasks }}
api: wb-work-with-products
method: GET
path: /api/v2/buffer/tasks
operation_id: get-api-v2-buffer-tasks
tags:
  - Цены и скидки
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 54eda4f7d76d9f5e
---

# Состояние необработанной загрузки{{ /api/v2/buffer/tasks }}

`GET /api/v2/buffer/tasks`

Описание метода Метод возвращает информацию про загрузку скидок в обработке. Необработанная загрузка — это загрузка скидок в календаре акций . Такие скидки применятся к товарам только в момент старта акции. Лимит запросов на один аккаунт продавца для всех методов категории Цены и скидки : | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов | | Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов | | Базовый с секретом | 6 сек | 10 запросов | 600 мс | 5 запросов | | Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос | В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента .

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `uploadID` | query | integer | да | ID загрузки |

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `uploadID` — integer. ID загрузки
  - `status` — integer. Статус загрузки: `1` — в обработке
  - `uploadDate` — string<date-time>. Дата и время, когда загрузка создана
  - `activationDate` — string<date-time>. Дата и время, когда загрузка отправляется в обработку
  - `overAllGoodsNumber` — integer. Всего товаров
  - `successGoodsNumber` — integer. Товаров без ошибок (0, потому что загрузка в обработке)
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**400** — Неправильный запрос

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**403** — Доступ запрещён

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
