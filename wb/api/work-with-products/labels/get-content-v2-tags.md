---
title: Список ярлыков
api: wb-work-with-products
method: GET
path: /content/v2/tags
operation_id: get-content-v2-tags
tags:
  - labels
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 72021100fef8a68c
---

# Список ярлыков

`GET /content/v2/tags`

Описание метода

Метод возвращает список и характеристики всех ярлыков продавца для группировки и фильтрации товаров.

Лимит запросов на один аккаунт продавца для всех методов Ярлыков:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Сервисный | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Ответы

**200** — Успешно

- `additionalErrors` — string. Дополнительные ошибки
- `data` — object
  - `color` — string. Цвет ярлыка
  - `id` — integer. Числовой ID ярлыка
  - `name` — string. Имя ярлыка
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

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
