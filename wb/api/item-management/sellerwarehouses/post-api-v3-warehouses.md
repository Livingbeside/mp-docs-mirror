---
title: Создать склад продавца
api: wb-item-management
method: POST
path: /api/v3/warehouses
operation_id: postV3Warehouses
tags:
  - sellerWarehouses
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: a1021fe8e68a149d
---

# Создать склад продавца

`POST /api/v3/warehouses`

Описание метода

Метод создаёт склад продавца для работы с [остатками товаров](./item-management#tag/sellerWarehousesInventory), кроме сверхгабаритных (СГТ), по модели [FBS](./orders-fbs) (Fulfillment by Seller).

Лимит запросов на один профиль продавца для всех методов складов продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `name` — string **обязательный**. Имя склада продавца
- `officeId` — integer **обязательный**. ID [склада WB](./item-management#tag/sellerWarehouses/operation/getV3Offices). Нельзя привязывать склад WB, который уже используется

## Ответы

**201** — Создано

- `id` — integer. ID склада продавца

**400** — Неправильный запрос

- `code` — string **обязательный**. Код ошибки
- `message` — string **обязательный**. Детали ошибки

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

- `code` — string **обязательный**. Код ошибки
- `message` — string **обязательный**. Детали ошибки

**404** — Не найдено

- `code` — string **обязательный**. Код ошибки
- `message` — string **обязательный**. Детали ошибки

**409** — Ошибка создания нового склада

- `code` — string **обязательный**. Код ошибки
- `message` — string **обязательный**. Детали ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
