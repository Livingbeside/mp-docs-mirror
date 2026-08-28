---
title: Список документов
api: wb-financial-reports-and-accounting
method: GET
path: /api/v1/documents/list
operation_id: getV1DocumentsList
tags:
  - documents
spec_version: finances
source: "https://dev.wildberries.ru/docs/openapi/financial-reports-and-accounting"
deprecated: false
content_sha: 5fe7d8d4f766b633
---

# Список документов

`GET /api/v1/documents/list`

Описание метода

Метод возвращает список документов продавца. Вы можете получить [один](./financial-reports-and-accounting#tag/documents/operation/getV1DocumentsDownload) или [несколько](./financial-reports-and-accounting#tag/documents/operation/postV1DocumentsDownloadAll) документов из полученного списка.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 10 сек | 1 запрос | 10 сек | 5 запросов |
| Сервисный | 10 сек | 1 запрос | 10 сек | 5 запросов |
| Базовый с секретом | 10 сек | 1 запрос | 10 сек | 5 запросов |
| Базовый | 24 ч | 1 запрос | 24 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `locale` | query | string | нет | Язык поля `category`: - `ru` — русский - `en` — английский - `zh` — китайский |
| `beginTime` | query | string<date> | нет | Начало периода. Только вместе с `endTime` |
| `endTime` | query | string<date> | нет | Конец периода. Только вместе с `beginTime` |
| `sort` | query | string (date, category) | нет | Сортировка: - `date` — по дате создания документа - `category` — по категории (только при `locale=ru`) Только вместе с `order` |
| `order` | query | string (desc, asc) | нет | Сортировка: - `desc` — по убыванию - `asc` — по возрастанию Только вместе с `sort` |
| `category` | query | string | нет | ID [категории документов](./financial-reports-and-accounting#tag/documents/operation/getV1DocumentsCategories) из поля `name` |
| `serviceName` | query | string | нет | Уникальный ID документа |
| `limit` | query | integer | нет | Максимальное количество строк ответа |
| `offset` | query | integer | нет | После какой строки выдавать данные |

## Ответы

**200** — Успешно

- `data` — object
  - `documents` — array[object]. Категории документов
    - `category` — string. Название [категории документов](./financial-reports-and-accounting#tag/documents/operation/getV1DocumentsCategories) из поля ответа `title`
    - `creationTime` — string. Дата и время создания документа
    - `extensions` — array[string]. Форматы документа
    - `name` — string. Название документа
    - `serviceName` — string. Уникальный ID документа
    - `viewed` — boolean. Выгружен ли документ в личном кабинете

**400** — Неправильный запрос

- `detail` — string. Детализация ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `title` — string. Заголовок ошибки

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
