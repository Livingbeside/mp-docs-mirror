---
title: Обновить остатки товаров{{ /api/v3/stocks/{warehouseId} }}
api: wb-work-with-products
method: PUT
path: /api/v3/stocks/{warehouseId}
operation_id: put-api-v3-stocks-warehouseid
tags:
  - Остатки на складах продавца
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 2b5ff8c19ddc0f2e
---

# Обновить остатки товаров{{ /api/v3/stocks/{warehouseId} }}

`PUT /api/v3/stocks/{warehouseId}`

Описание метода

Метод обновляет количество остатков товаров продавца [в списке](./work-with-products#tag/Ostatki-na-skladah-prodavca/paths/~1api~1v3~1stocks~1%7BwarehouseId%7D/post).

 Названия параметров запроса не валидируются. При отправке некорректных названий вы получите успешный ответ (204), но остатки не обновятся.

Лимит запросов на один аккаунт продавца для всех методов остатков на складах продавца кроме метода удаления остатков:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `warehouseId` | path | integer<int64> | да | ID склада продавца |

## Запрос

**Тело запроса** (`application/json`):

- `stocks` — array[object] **обязательный**. Массив ID размеров товаров и их остатков
  - `amount` — integer. Остаток
  - `chrtId` — integer. ID размера товара

## Ответы

**204** — Обновлено

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

**406** — Обновление остатков заблокировано

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**409** — Ошибка обновления остатков

- `code` — string. Код ошибки
- `data` — array[object]. Дополнительная информация об ошибке
  - `amount` — integer. Остаток
  - `chrtId` — integer. ID размера товара
  - `sku` — string. Баркод
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
