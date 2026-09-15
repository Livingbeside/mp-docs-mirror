---
title: Состояние обработанной загрузки
api: wb-item-management
method: GET
path: /api/v2/history/tasks
operation_id: getV2HistoryTasks
tags:
  - pricesAndDiscounts
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: b8b67198f105a1cd
---

# Состояние обработанной загрузки

`GET /api/v2/history/tasks`

Описание метода

Метод возвращает информацию об обработанной загрузке цен и скидок.

 Обработанная загрузка — это загрузка цен и скидок для [товаров](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTask), цен для [размеров товаров](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTaskSize), [скидок WB Клуба](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTaskClubDiscount) и [оптовых скидок для B2B-продаж](./item-management#tag/pricesAndDiscounts/operation/postV1UploadTaskB2bWholesale).

Лимит запросов на один аккаунт продавца для всех методов категории Цены и скидки:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `uploadID` | query | integer | да | ID загрузки |

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `uploadID` — integer. ID загрузки
  - `status` — integer. Статус загрузки: * `3` — обработана, в товарах нет ошибок, цены и скидки обновились * `4` — отменена * `5` — обработана, но в товарах есть ошибки. Для товаров без ошибок цены и скидки обновились, а ошибки в остальных товарах можно получить с помощью метода [Детализация обработанной загрузки](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryGoodsTask) * `6` — обработана, но во всех товарах есть ошибки. Их тоже можно получить с помощью метода [Детализация обработанной загрузки](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryGoodsTask)
  - `uploadDate` — string<date-time>. Дата и время, когда загрузка создана
  - `activationDate` — string<date-time>. Дата и время, когда загрузка отправляется в обработку
  - `overAllGoodsNumber` — integer. Всего товаров
  - `successGoodsNumber` — integer. Товаров без ошибок
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
