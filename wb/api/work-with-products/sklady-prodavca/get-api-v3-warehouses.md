---
title: Получить список складов продавца{{ /api/v3/warehouses }}
api: wb-work-with-products
method: GET
path: /api/v3/warehouses
operation_id: get-api-v3-warehouses
tags:
  - Склады продавца
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: e31baf39cef8306a
---

# Получить список складов продавца{{ /api/v3/warehouses }}

`GET /api/v3/warehouses`

Описание метода Метод возвращает список всех складов продавца. Может использоваться для работы с [остатками товаров](./work-with-products#tag/Ostatki-na-skladah-prodavca). Лимит запросов на один аккаунт продавца для всех методов складов продавца : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента .

## Ответы

**200** — Успешно

- `name` — string. Название склада продавца
- `officeId` — integer<int64>. ID склада WB
- `id` — integer<int64>. ID склада продавца
- `cargoType` — integer (1, 2, 3). Тип товара: - `1` — малогабаритный товар (МГТ) - `2` — сверхгабаритный товар (СГТ) - `3` — крупногабаритный товар (КГТ+)
- `deliveryType` — integer (1, 2, 3, 5, 6). Тип доставки, который принимает склад: - `1` — доставка на склад WB (FBS) - `2` — доставка силами продавца (DBS) - `3` — доставка курьером WB (DBW) - `5` — самовывоз (C&C) - `6` — экспресс-доставка силами продавца (ЕDBS)
- `isDeleting` — boolean. Склад удаляется: - `false` — нет - `true` — да После удаления склад пропадёт из списка
- `isProcessing` — boolean. Данные склада обновляются: - `false` — нет - `true` — да, обновление и удаление остатков недоступно Обновление данных может занимать несколько минут

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
