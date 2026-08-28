---
title: Удаление ярлыка{{ /content/v2/tag/{id} }}
api: wb-work-with-products
method: DELETE
path: /content/v2/tag/{id}
operation_id: delete-content-v2-tag-id
tags:
  - labels
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 81c0d770adac378e
---

# Удаление ярлыка{{ /content/v2/tag/{id} }}

`DELETE /content/v2/tag/{id}`

Описание метода

Метод удаляет ярлык из [списка ярлыков](./work-with-products#tag/labels/paths/~1content~1v2~1tags/get) продавца.

Лимит запросов на один аккаунт продавца для всех методов Ярлыков:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Сервисный | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `id` | path | integer | да | Числовой ID ярлыка |

## Ответы

**200** — Успешно

- `additionalErrors` — string. Дополнительные ошибки
- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**400** — Неправильный запрос

- `additionalErrors` — object. Дополнительные ошибки
- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

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

- `additionalErrors` — string. Дополнительные ошибки
- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
