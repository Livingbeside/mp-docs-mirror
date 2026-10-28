---
title: Получить рейтинг продавца
api: wb-api-information
method: GET
path: /api/common/v1/rating
operation_id: getV1Rating
tags:
  - sellerInformation
spec_version: general
source: "https://dev.wildberries.ru/docs/openapi/api-information"
deprecated: false
content_sha: 87ba11f05838b6b2
---

# Получить рейтинг продавца

`GET /api/common/v1/rating`

Описание метода

 Для доступа к методу используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Вопросы и отзывы

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Сервисному токену

Метод возвращает пользовательский рейтинг продавца и количество отзывов.

Лимит запросов на один профиль продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1 запрос | 1 мин | 1 запрос |

## Ответы

**200** — Успешно

- `feedbackCount` — integer. Количество отзывов
- `valuation` — number<float>. Рейтинг продавца

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

- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string **обязательный**. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string **обязательный**. ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `status` — number **обязательный**. HTTP статус-код
- `statusText` — string **обязательный**. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time> **обязательный**. Дата и время запроса

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
