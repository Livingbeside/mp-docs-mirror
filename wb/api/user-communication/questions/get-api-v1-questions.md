---
title: Список вопросов{{ /api/v1/questions }}
api: wb-user-communication
method: GET
path: /api/v1/questions
operation_id: getV1Questions
tags:
  - questions
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: d4e2c83c032e006c
---

# Список вопросов{{ /api/v1/questions }}

`GET /api/v1/questions`

Описание метода Метод возвращает список вопросов по заданным фильтрам. Вы можете: - получить данные отвеченных и неотвеченных вопросов - сортировать вопросы по дате - настроить пагинацию и количество вопросов в ответе Можно получить максимум 10 000 вопросов в одном ответе Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы : | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов | | Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов | | Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов | | Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `isAnswered` | query | boolean | да | Есть ли ответ на вопрос: - `true` — да - `false` — нет |
| `nmId` | query | integer | нет | Артикул WB |
| `take` | query | integer | да | Количество запрашиваемых вопросов (максимально допустимое значение для параметра - 10 000, при этом сумма значений параметров `take` и `skip` не должна превышать 10 000) |
| `skip` | query | integer | да | Количество вопросов для пропуска (максимально допустимое значение для параметра - 10 000, при этом сумма значений параметров `take` и `skip` не должна превышать 10 000) |
| `order` | query | string | нет | Сортировка вопросов по дате (`dateAsc`/`dateDesc`) |
| `dateFrom` | query | integer | нет | Дата начала периода в формате Unix timestamp |
| `dateTo` | query | integer | нет | Дата конца периода в формате Unix timestamp |

## Ответы

**200** — Успешно

- `data` — object
  - `countUnanswered` — integer. Количество неотвеченных вопросов
  - `countArchive` — integer. Количество отвеченных вопросов
  - `questions` — array[object]. Вопросы
    - `id` — string. id вопроса
    - `text` — string. Текст вопроса
    - `createdDate` — string<date-time>. Дата и время создания вопроса
    - `state` — string. Статус вопроса: - `none` — вопрос отклонён продавцом (такой вопрос не отображается на портале покупателей) - `wbRu` — ответ предоставлен, вопрос отображается на сайте покупателей - `suppliersPortalSynch` - новый вопрос
    - `answer` — object. Структура ответа
      - `text` — string. Текст ответа
      - `editable` — boolean. Можно ли отредактировать ответ (`false` - нельзя, `true` - можно)
      - `createDate` — string<date-time>. Дата и время создания ответа
    - `productDetails` — object. Информация о товаре
      - `nmId` — integer. Артикул WB
      - `imtId` — integer. ID для [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров
      - `productName` — string. Название товара
      - `supplierArticle` — string. Артикул продавца
      - `supplierName` — string. Имя продавца
      - `brandName` — string. Название бренда
    - `wasViewed` — boolean. Просмотрен ли вопрос
    - `isWarned` — boolean. Признак подозрительного вопроса. Если `true`, то вопрос опубликован, но на портале продавцов вы увидите баннер **Сообщение подозрительное**
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки

**400** — Неправильный запрос

- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки
- `requestId` — string

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

- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки
- `requestId` — string

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
