---
title: Получить информацию о подписке Джем
api: wb-api-information
method: GET
path: /api/common/v1/subscriptions
operation_id: getV1Subscriptions
tags:
  - sellerInformation
spec_version: general
source: "https://dev.wildberries.ru/docs/openapi/api-information"
deprecated: false
content_sha: 01c827612d17967f
---

# Получить информацию о подписке Джем

`GET /api/common/v1/subscriptions`

Описание метода

 Информацию о подписке Джем можно получить с токеном любой категории

 Метод доступен по
 Сервисному токену

Метод возвращает информацию о подписке [Джем](https://seller.wildberries.ru/monetization/jam):
 - Если продавец никогда не подключал подписку Джем, возвращается пустой ответ `200`.
 - Если продавец активировал и никогда не отменял подписку, возвращается:
 - дата активации подписки `since`
 - дата окончания текущего оплаченного периода `till`
 - Если подписка закончилась или была отменена, но продавец подключил её повторно, возвращается:
 - дата первой активации подписки `since`
 - дата окончания текущего оплаченного периода `till`
 - Если подписка неактивна, возвращается:
 - дата первой активации подписки `since`
 - дата окончания последнего оплаченного периода `till`

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1 запрос | 1 мин | 10 запросов |

## Ответы

**200** — Успешно

- `activationSource` — string (constructor, jam) **обязательный**. Источник подключения подписки: - `constructor` — покупка через раздел **Конструктор тарифов** - `jam` — покупка через раздел **Подписка «Джем»**
- `level` — string (standard, advanced, premium) **обязательный**. Уровень подписки: - `standard` - `advanced` - `premium`
- `since` — string<date-time> **обязательный**. Дата и время первой активации подписки. Не меняется при продлении или повторной активации
- `state` — string (active, inactive) **обязательный**. Статус подписки: - `active` — активна - `inactive` — истекла или отменена
- `till` — string<date-time> **обязательный**. Дата и время окончания подписки

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

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
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
