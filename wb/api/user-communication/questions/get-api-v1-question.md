---
title: Получить вопрос по ID
api: wb-user-communication
method: GET
path: /api/v1/question
operation_id: getV1Question
tags:
  - questions
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: a2ec9f82c7c7324c
---

# Получить вопрос по ID

`GET /api/v1/question`

Описание метода

Метод возвращает данные [вопроса](./user-communication#tag/questions/operation/getV1Questions) по его ID. Далее вы можете [работать с этим вопросом](./user-communication#tag/questions/operation/patchV1Questions).

Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `id` | query | string | да | ID вопроса |

## Ответы

**200** — Успешно

- `additionalErrors` — array[string]. Дополнительные ошибки
- `data` — object
  - `answer` — object. Ответ
    - `createDate` — string<date-time>. Дата и время создания ответа
    - `editable` — boolean. Можно ли отредактировать ответ (`false` - нельзя, `true` - можно)
    - `text` — string. Текст ответа
  - `createdDate` — string<date-time>. Дата и время создания вопроса
  - `id` — string. ID вопроса
  - `isWarned` — boolean. Признак подозрительного вопроса. Если `true`, то вопрос опубликован, но на портале продавцов вы увидите баннер **Сообщение подозрительное**
  - `productDetails` — object. Item information
    - `brandName` — string. Название бренда
    - `imtId` — integer. ID для [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров
    - `nmId` — integer. Артикул WB
    - `productName` — string. Название товара
    - `supplierArticle` — string. Артикул продавца
    - `supplierName` — string. Имя продавца
  - `state` — string. Статус вопроса: - `none` - вопрос отклонён продавцом (такой вопрос не отображается на портале покупателей) - `wbRu` - ответ предоставлен, вопрос отображается на сайте покупателей - `suppliersPortalSynch` - новый вопрос
  - `text` — string. Текст вопроса
  - `wasViewed` — boolean. Просмотрен ли вопрос
- `error` — boolean. Есть ли ошибка
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

- `additionalErrors` — array[string]. Дополнительные ошибки
- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `requestId` — string

**422** — Ошибка обработки параметров запроса

- `additionalErrors` — array[string]. Дополнительные ошибки
- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `requestId` — string

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
