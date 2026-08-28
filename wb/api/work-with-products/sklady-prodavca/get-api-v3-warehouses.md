---
title: Получить список складов продавца
api: wb-work-with-products
method: GET
path: /api/v3/warehouses
operation_id: get-api-v3-warehouses
tags:
  - Склады продавца
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: c46a579d6604b4f3
---

# Получить список складов продавца

`GET /api/v3/warehouses`

Описание метода

Метод возвращает список всех складов продавца. Может использоваться для работы с [остатками товаров](./work-with-products#tag/Ostatki-na-skladah-prodavca).

Лимит запросов на один аккаунт продавца для всех методов складов продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Ответы

**200** — Успешно

- `cargoType` — integer (1, 2, 3). Тип товара: - `1` — малогабаритный товар (МГТ) - `2` — сверхгабаритный товар (СГТ) - `3` — крупногабаритный товар (КГТ+)
- `deliveryType` — integer (1, 2, 3, 5, 6). Тип доставки, который принимает склад: - `1` — доставка на склад WB (FBS) - `2` — доставка силами продавца (DBS) - `3` — доставка курьером WB (DBW) - `5` — самовывоз (C&C) - `6` — экспресс-доставка силами продавца (ЕDBS)
- `id` — integer<int64>. ID склада продавца
- `isDeleting` — boolean. Склад удаляется: - `false` — нет - `true` — да После удаления склад пропадёт из списка
- `isProcessing` — boolean. Данные склада обновляются: - `false` — нет - `true` — да, обновление и удаление остатков недоступно Обновление данных может занимать несколько минут
- `name` — string. Название склада продавца
- `officeId` — integer<int64>. ID склада WB

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
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
