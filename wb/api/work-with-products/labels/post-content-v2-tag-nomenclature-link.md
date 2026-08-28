---
title: Управление ярлыками в карточке товара{{ /content/v2/tag/nomenclature/link }}
api: wb-work-with-products
method: POST
path: /content/v2/tag/nomenclature/link
operation_id: post-content-v2-tag-nomenclature-link
tags:
  - labels
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 43dbde7344e4f8b4
---

# Управление ярлыками в карточке товара{{ /content/v2/tag/nomenclature/link }}

`POST /content/v2/tag/nomenclature/link`

Описание метода Метод добавляет или снимает ярлык с карточки товара. К карточке можно добавить максимум 15 ярлыков. При удалении ярлыка из карточки товара он не удаляется из [списка ярлыков](./work-with-products#tag/labels/paths/~1content~1v2~1tags/get) продавца. Лимит запросов на один аккаунт продавца для всех методов Ярлыков : | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 100 запросов | 600 мс | 5 запросов | | Сервисный | 1 мин | 100 запросов | 600 мс | 5 запросов | | Базовый с секретом | 1 мин | 100 запросов | 600 мс | 5 запросов | | Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос | В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента .

## Запрос

**Тело запроса** (`application/json`):

- `nmID` — integer. Артикул WB
- `tagsIDs` — array[integer]. Массив числовых ID ярлыков. Что бы снять ярлыки с карточки товара, необходимо передать пустой массив. Чтобы добавить ярлыки к уже имеющимся в карточке товара, необходимо в запросе передать новые ярлыки и ярлыки, которые уже есть в карточке товара.

## Ответы

**200** — Успешно

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки
- `additionalErrors` — string. Дополнительные ошибки

**400** — Неправильный запрос

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки
- `additionalErrors` — string. Дополнительные ошибки

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

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки
- `additionalErrors` — string. Дополнительные ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
