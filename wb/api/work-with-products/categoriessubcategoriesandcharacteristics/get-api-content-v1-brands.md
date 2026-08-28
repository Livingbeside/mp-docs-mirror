---
title: Бренды
api: wb-work-with-products
method: GET
path: /api/content/v1/brands
operation_id: get-api-content-v1-brands
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 01eacc566d031fac
---

# Бренды

`GET /api/content/v1/brands`

Описание метода

Метод возвращает список брендов по ID предмета.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Сервисный | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Базовый с секретом | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `subjectId` | query | integer | да | ID предмета |
| `next` | query | integer | нет | Параметр пагинации. Используйте значение `next` из ответа, чтобы получить следующий пакет данных |

## Ответы

**200** — Успешно

- `brands` — array[object] **обязательный**
  - `id` — integer **обязательный**. ID бренда
  - `logoUrl` — string **обязательный**. URL логотипа бренда
  - `name` — string **обязательный**. Название бренда
- `next` — integer. Параметр пагинации. Укажите это значение в запросе, чтобы получить следующий пакет данных. Если поле отсутствует, вы получили все данные
- `total` — integer **обязательный**. Общее количество брендов предмета

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `errors` — array[object]
  - `location` — string. Параметр, где произошла ошибка
  - `message` — string. Текст ошибки
  - `value` — ?. Значение параметра, где произошла ошибка
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**404** — Не найдено

- `detail` — string **обязательный**. Детали ошибки
- `errors` — array[object]
  - `location` — string. Параметр, где произошла ошибка
  - `message` — string. Текст ошибки
  - `value` — ?. Значение параметра, где произошла ошибка
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
