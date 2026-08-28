---
title: Удалить остатки товаров{{ /api/v3/stocks/{warehouseId} }}
api: wb-work-with-products
method: DELETE
path: /api/v3/stocks/{warehouseId}
operation_id: delete-api-v3-stocks-warehouseid
tags:
  - Остатки на складах продавца
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 354be1251512390d
---

# Удалить остатки товаров{{ /api/v3/stocks/{warehouseId} }}

`DELETE /api/v3/stocks/{warehouseId}`

Описание метода

Метод удаляет запись об остатках товаров продавца из [списка остатков](./work-with-products#tag/Ostatki-na-skladah-prodavca/paths/~1api~1v3~1stocks~1%7BwarehouseId%7D/post).

 Действие необратимо. Удаленный остаток будет необходимо загрузить повторно для возобновления продаж.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 10 запросов | 6 сек | 2 запроса |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `warehouseId` | path | integer<int64> | да | ID склада продавца |

## Запрос

**Тело запроса** (`application/json`):

- `chrtIds` — array[integer] **обязательный**. Массив ID размеров товаров

## Ответы

**204** — Удалено

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

**409** — Ошибка удаления остатков

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
