---
title: Получение истории затрат{{ /adv/v1/upd }}
api: wb-promotion
method: GET
path: /adv/v1/upd
operation_id: getV1Upd
tags:
  - finances
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: f5eb5baa32545bbf
---

# Получение истории затрат{{ /adv/v1/upd }}

`GET /adv/v1/upd`

Описание метода Метод формирует список фактических затрат на рекламные кампании за заданный период. Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 сек | 1 запрос | 1 сек | 5 запросов | | Сервисный | 1 сек | 1 запрос | 1 сек | 5 запросов | | Базовый с секретом | 1 сек | 1 запрос | 1 сек | 5 запросов | | Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `from` | query | string<date> | да | Начало интервала |
| `to` | query | string<date> | да | Конец интервала. (Минимальный интервал 1 день, максимальный 31) |

## Ответы

**200** — Успешно

- `updNum` — integer. Номер выставленного документа
- `updTime` — string<time-date>. Время списания
- `updSum` — integer. Выставленная сумма в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `advertId` — integer. ID кампании
- `campName` — string. Название кампании
- `advertType` — integer. Тип кампании
- `paymentType` — string. Источник списания: - `Баланс` - `Бонусы` - `Счёт` - `Кэшбэк`
- `advertStatus` — integer. Статус кампании: - `-1` — удалена, процесс удаления будет завершён в течение 10 минут - `4` — готова к запуску - `7` — завершена - `8` — отменена - `9` — активна - `11` — на паузе

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
