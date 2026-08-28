---
title: Получить информацию о продавце{{ /api/v1/seller-info }}
api: wb-api-information
method: GET
path: /api/v1/seller-info
operation_id: getV1SellerInfo
tags:
  - sellerInformation
spec_version: general
source: "https://dev.wildberries.ru/docs/openapi/api-information"
deprecated: false
content_sha: f395cffd27cb5ce8
---

# Получить информацию о продавце{{ /api/v1/seller-info }}

`GET /api/v1/seller-info`

Описание метода Информацию о продавце можно получить с токеном любой категории Метод позволяет получать наименование продавца и ID его профиля. Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 1 запрос | 1 мин | 10 запросов | | Сервисный | 1 мин | 1 запрос | 1 мин | 10 запросов | | Базовый с секретом | 1 мин | 1 запрос | 1 мин | 10 запросов | | Базовый | 24 ч | 1 запрос | 24 ч | 1 запрос |

## Ответы

**200** — Успешно

- `name` — string. Наименование продавца
- `sid` — string<UUID>. Уникальный ID продавца на Wildberries, [находящийся в публичном поле токена](./api-information#tag/authorization/Kak-ustroen-token)
- `tin` — string. ИНН
- `tradeMark` — string. Торговое наименование продавца

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
