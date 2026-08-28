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
content_sha: da8e2ed3c1cc2863
---

# Получить информацию о подписке Джем

`GET /api/common/v1/subscriptions`

Описание метода

 Информацию о подписке Джем можно получить с токеном любой [категории](./api-information#tag/authorization/Kategorii-tokenov)

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
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

- `state` — string (active, inactive) **обязательный**. Статус подписки: - `active` — активна - `inactive` — истекла или отменена
- `activationSource` — string (constructor, jam) **обязательный**. Источник подключения подписки: - `constructor` — покупка через раздел **Конструктор тарифов** - `jam` — покупка через раздел **Подписка «Джем»**
- `level` — string (standard, advanced, premium) **обязательный**. Уровень подписки: - `standard` - `advanced` - `premium`
- `since` — string<date-time> **обязательный**. Дата и время первой активации подписки. Не меняется при продлении или повторной активации
- `till` — string<date-time> **обязательный**. Дата и время окончания подписки

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

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
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
