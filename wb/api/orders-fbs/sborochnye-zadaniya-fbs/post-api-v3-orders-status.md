---
title: Получить статусы сборочных заданий
api: wb-orders-fbs
method: POST
path: /api/v3/orders/status
operation_id: post-api-v3-orders-status
tags:
  - Сборочные задания FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: bd2c9f5acaad7a7a
---

# Получить статусы сборочных заданий

`POST /api/v3/orders/status`

Описание метода

Метод возвращает статусы [сборочных заданий](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders/get) по их ID.

`supplierStatus` — статус сборочного задания. Триггер его изменения — действие самого продавца.

Возможные значения `supplierStatus`:

| Статус | Описание | Как перевести сборочное задание в данный статус |
|-------|----------------------|--------------------------------------|
| `new` | **Новое сборочное задание** | |
| `confirm` | **На сборке** |[Добавить сборочное задание к поставке](./orders-fbs#tag/Postavki-FBS/paths/~1api~1marketplace~1v3~1supplies~1%7BsupplyId%7D~1orders/patch)
| `complete` | **В доставке** | [Передать поставку в доставку](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D~1deliver/patch) |
| `cancel` | **Отменено продавцом** | [Отменить сборочное задание](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1%7BorderId%7D~1cancel/patch)|
| `cancel_carrier` | **Отменено перевозчиком** <br>Только для трансграничных поставок | Переводится перевозчиком |

`wbStatus` — статус системы Wildberries.

Возможные значения `wbStatus`:
- `waiting` — сборочное задание в работе
- `sorted` — сборочное задание отсортировано
- `sold` — заказ получен покупателем
- `canceled` — отмена сборочного задания
- `canceled_by_client` — покупатель отменил заказ при получении
- `declined_by_client` — покупатель отменил заказ. Отмена доступна покупателю в первый час с момента заказа, если заказ не переведён на сборку
- `defect` — отмена заказа по причине брака
- `ready_for_pickup` — заказ прибыл на пункт выдачи заказов (ПВЗ)
- `accepted_by_carrier` — продавец передал заказ в службу доставки в своей стране
- `sent_to_carrier` — заказ отправлен на склад службы доставки в стране продавца
- `canceled_by_carrier` — заказ отменён перевозчиком. Только для трансграничных поставок

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer<int64>] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `orders` — array[object]
  - `id` — integer<int64>. ID сборочного задания
  - `isCancellable` — boolean. Доступна ли [отмена](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1%7BorderId%7D~1cancel/patch) сборочного задания: - `false` — недоступна - `true` — доступна
  - `supplierStatus` — string (new, confirm, complete, cancel). Статус сборочного задания, установленный продавцом
  - `wbStatus` — string (waiting, sorted, sold, canceled, canceled_by_client, declined_by_client, defect, ready_for_pickup, postponed_delivery, accepted_by_carrier, sent_to_carrier). Статус сборочного задания в системе Wildberries

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

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

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
