---
title: Получение истории затрат
api: wb-promotion
method: GET
path: /adv/v1/upd
operation_id: getV1Upd
tags:
  - finances
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 964c65105f17bc46
---

# Получение истории затрат

`GET /adv/v1/upd`

Описание метода

Метод формирует список фактических затрат на рекламные кампании за заданный период.

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
| `from` | query | string<date> | да | Начало интервала |
| `to` | query | string<date> | да | Конец интервала. (Минимальный интервал 1 день, максимальный 31) |

## Ответы

**200** — Успешно

- `advertId` — integer. ID кампании
- `advertStatus` — integer. Статус кампании: - `-1` — удалена, процесс удаления будет завершён в течение 10 минут - `4` — готова к запуску - `7` — завершена - `8` — отменена - `9` — активна - `11` — на паузе
- `advertType` — integer. Тип кампании
- `campName` — string. Название кампании
- `paymentType` — string. Источник списания: - `Баланс` - `Бонусы` - `Счёт` - `Кэшбэк`
- `updNum` — integer. Номер выставленного документа
- `updSum` — integer. Выставленная сумма в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `updTime` — string<time-date>. Время списания

**400** — Неправильный запрос

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
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
