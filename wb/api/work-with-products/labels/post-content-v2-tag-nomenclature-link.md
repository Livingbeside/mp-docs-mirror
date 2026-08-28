---
title: Управление ярлыками в карточке товара
api: wb-work-with-products
method: POST
path: /content/v2/tag/nomenclature/link
operation_id: post-content-v2-tag-nomenclature-link
tags:
  - labels
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: e2a08117d1b74bef
---

# Управление ярлыками в карточке товара

`POST /content/v2/tag/nomenclature/link`

Описание метода

Метод добавляет или снимает ярлык с карточки товара. К карточке можно добавить максимум 15 ярлыков.

При удалении ярлыка из карточки товара он не удаляется из [списка ярлыков](./work-with-products#tag/labels/paths/~1content~1v2~1tags/get) продавца.

Лимит запросов на один аккаунт продавца для всех методов Ярлыков:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Сервисный | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Запрос

**Тело запроса** (`application/json`):

- `nmID` — integer. Артикул WB
- `tagsIDs` — array[integer]. Массив числовых ID ярлыков. Что бы снять ярлыки с карточки товара, необходимо передать пустой массив. Чтобы добавить ярлыки к уже имеющимся в карточке товара, необходимо в запросе передать новые ярлыки и ярлыки, которые уже есть в карточке товара.

## Ответы

**200** — Успешно

- `additionalErrors` — string. Дополнительные ошибки
- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**400** — Неправильный запрос

- `additionalErrors` — string. Дополнительные ошибки
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
