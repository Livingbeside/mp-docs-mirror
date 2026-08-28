---
title: Получение новостей портала продавцов{{ /api/communications/v2/news }}
api: wb-api-information
method: GET
path: /api/communications/v2/news
operation_id: getV2News
tags:
  - newsApi
spec_version: general
source: "https://dev.wildberries.ru/docs/openapi/api-information"
deprecated: false
content_sha: 07f748ab0f2b6c12
---

# Получение новостей портала продавцов{{ /api/communications/v2/news }}

`GET /api/communications/v2/news`

Описание метода Метод позволяет получать новости портала продавцов. Для получения успешного ответа необходимо указать один из параметров `from` или `fromID`. За один запрос можно получить не более 100 новостей. Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 1 запрос | 1 мин | 10 запросов | | Сервисный | 1 мин | 1 запрос | 1 мин | 10 запросов | | Базовый с секретом | 1 мин | 1 запрос | 1 мин | 10 запросов | | Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `from` | query | string<date> | нет | Дата, от которой необходимо выдать новости |
| `fromID` | query | integer<uint64> | нет | ID новости, начиная с которой — включая её — нужно получить список новостей |

## Ответы

**200** — Успешно

- `data` — array[object]. Новости
  - `content` — string<plaintext>. Текст новости
  - `date` — string<date-time>. Дата и время публикации новости
  - `header` — string. Заголовок новости
  - `id` — integer. ID новости
  - `types` — array[object]. Теги новости
    - `id` — integer. ID тега
    - `name` — string. Название тега

**400** — Неправильный запрос

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
