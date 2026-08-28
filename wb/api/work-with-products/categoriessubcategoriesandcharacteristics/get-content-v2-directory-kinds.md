---
title: Пол
api: wb-work-with-products
method: GET
path: /content/v2/directory/kinds
operation_id: get-content-v2-directory-kinds
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 0a99ad5e51fc46a4
---

# Пол

`GET /content/v2/directory/kinds`

Описание метода

Метод возвращает возможные значения [характеристики](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1object~1charcs~1%7BsubjectId%7D/get) предмета `Пол`.

Лимит запросов на один аккаунт продавца для методов Характеристик:

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
| `locale` | query | string | нет | Язык полей ответа `subjectName` и `name`: - `ru` — русский - `en` — английский - `zh` — китайский Не используется в песочнице. Данные песочницы возвращаются только на русском языке |

## Ответы

**200** — Успешно

- `additionalErrors` — string. Дополнительные ошибки
- `data` — array[string]. Массив значений для хар-ки Пол
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

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
